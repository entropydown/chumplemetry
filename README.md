# chumplemetry

## the physical hardware box
  * has gps antenna
  * external power (usb power, hardwire)
  * 4g sim for upload of telemetry strings to "cloud"
  * wifi for debug mode
  * some internal memory for buffering
  * N analog opto-isolated electrical inputs
  * 3 axis accelerometer (0g-2g)
  * gps at least 10hz update rate capable
  * N warning outputs: probably wired to some leds
  * N general purpose outputs: at least one wired to led to indicate shift rpm
  * computation limited to sampling analog inputs, determining warning thresholds, constructing and uploading telemetry string
  * determine if a warning output should be triggered based on the value from one of the N analog inputs
  * determine if a general purpose output should be triggered based on the value from one of the N analog inputs
  * generate a telemetry string from the analog inputs, accelerometer, gps at a configurable interval
  * upload the telemetry string to the "cloud" at a configurable interval
  * poll the cloud for "configuration"
  * some mechanism to update software (update from sd card / usb)
  * has physical ruggedness:
    * high vibration
    * dust
    * water?

## the "cloud" software
  * feeds the telemetry strings to kibana
    * visualize a bunch of stuff
  * parse the telemetry strings to display ui stuff
    * visual of track from gps data
    * heatmap of selectable data channel overlaid onto track visual
    * display of analog input values
  * data is labeled by driver (the person)
  * compare driver to driver or lap to lap
  * "push" configuration to the physical hardware box:
     * sample rates of each analog input
     * how to interpret the analog signals e.g. voltage based, resistance based and calibration e.g 2v-5v
     * labels for each analog input
     * sample rate of gps
     * sample rate of accelerometer
     * warning thresholds for each input

## cool, optional (?) features
  * display current laptime
  * display predictive laptime (are you currently slower or faster than the fastest lap or last lap (configurable))
  * export to vbo (circuit tools file format)
  * gopro lap trigger
    * upon the completion of a lap, make the gopro start a new file. The end result is 1 video file per lap.
    * The telemetry string has the corresponding video file name included for easy reference later
    * super optional
      * upload video of lap in real time; scroll data in ui and the video is scrolled and displayed side-by-side
