cordova-plugin-magnetometer
====================

![Coin Detector](https://raw.githubusercontent.com/sdesalas/cordova-magnetometer-app/master/design/screenshots/CoinDetector.jpg)

A magnetic field detector plugin ideal for science toolkit or metal detector apps. 
    
The API can be accessed via single call or by placing a listener that fires a callback function repeatedly. 

It displays the raw `x`, `y`, and `z` magnetometer values as well as a computed `magnitude` of the magnetic field.

- iOS Support by [Rameez Raja](https://github.com/mrameezraja)
- Android Support by [Steven de Salas](https://github.com/sdesalas)

See [this page](https://github.com/sdesalas/cordova-magnetometer-app/blob/master/android/magnetometer-harness/assets/www/index.html) for a basic sample cordova app using this plugin. 

Installation
------------

<code> cordova plugin add https://github.com/sdesalas/cordova-plugin-magnetometer </code>

Constants
-------
- cordova.plugins.magnetometer.SENSOR_DELAY_FASTEST (0 microsecond)
- cordova.plugins.magnetometer.SENSOR_DELAY_GAME (20,000 microsecond)
- cordova.plugins.magnetometer.SENSOR_DELAY_UI (60,000 microsecond)
- cordova.plugins.magnetometer.SENSOR_DELAY_NORMAL (200,000 microseconds)

Methods
-------
- cordova.plugins.magnetometer.getReading
- cordova.plugins.magnetometer.setSamplingPeriod
- cordova.plugins.magnetometer.watchReadings
- cordova.plugins.magnetometer.stop


cordova.plugins.magnetometer.setSamplingPeriod
-------------------------------------------

Sets frequency in microseconds at which magnetometer sensor readings should be updated.

<pre>
<code>
  cordova.plugins.magnetometer.setSamplingPeriod(
    function success(reading){
      console.log(JSON.stringify(reading)); 
      // Output: {x: 23.113, y:-37.245, z:6.172, magnitude: 44.266}
    }, 
    function error(message){
     console.log(message);
    },
    cordova.plugins.magnetometer.SENSOR_DELAY_NORMAL // Constant indicating frequency in microseconds at which magnetometer sensor readings should be updated.
  )
</code>
</pre>

`reading` object properties:
- `x`
- `y`
- `z`
- `magnitude` (calculated total - always positive)


cordova.plugins.magnetometer.getReading
-------------------------------------------

Gets a single reading from the magenetometer sensor.

<pre>
<code>
  cordova.plugins.magnetometer.getReading(
    function success(reading){
      console.log(JSON.stringify(reading)); 
      // Output: {x: 23.113, y:-37.245, z:6.172, magnitude: 44.266}
    }, 
    function error(message){
     console.log(message);
    }
  )
</code>
</pre>


cordova.plugins.magnetometer.watchReadings
-------------------------------------------

Gets regular magnetometer readings sent by the internal sensor, will fire success callback repeatedly.

<pre>
<code>
  var watchID = cordova.plugins.magnetometer.watchReadings(
    function success(reading){
      console.log(JSON.stringify(reading)); 
      // Output: {x: 23.113, y:-37.245, z:6.172, magnitude: 44.266}
    }, 
    function error(message){
     console.log(message);
    },
    {frequency:40} // Frequency in ms to check magnetometer sensor readings.
  )
</code>
</pre>

`reading` object properties:
- `x`
- `y`
- `z`
- `magnitude` (calculated total - always positive)

cordova.plugins.magnetometer.stop
--------------------------------

Stops getting readings from the magnetometer sensor. Optional watchID parameter.

<pre>
<code>
  cordova.plugins.magnetometer.stop([watchID])
</code>
</pre>

Supported Platforms
-------------------

- iOS
- Android 

