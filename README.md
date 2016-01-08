# chumplemetry

## the physical hardware box
  * mounted in cg of car
  * has gps antenna
  * hardwired power from car
  * 4g sim for upload of telemetry strings to "cloud"
  * some internal memory for buffering
  * N analog opto-isolated electrical inputs
  * 3 axis acclorometer (0g-2g)
  * gps at least 10hz update rate capable
  * N warning light outputs: probably wired to some leds
  * N general purpose light outputs: at least one wired to led to indicate shift rpm
  * determine if a warning light should be lit based on the value from one of the N analog inputs
  * determine if a general purpose light should be lit based on the value from one of the N analog inputs
  * generates a telemetry string from the analog inputs, acclorometer, gps at a configurable interval
  * uploads the telemetry string to the "cloud" at a configurable interval
  * polls the cloud for "configuration"

## the "cloud" software
  * feeds the telemetry strings to kibana
    * visualize a bunch of stuff
  * parse the telemetry strings to display ui stuff
    * visual of track from gps data
    * heatmap of selectable data channel overlayed onto track visual
    * display of analog input values
  * data is labeled by driver
  * compare driver to driver or lap to lap
  * "push" configuration to the physical hardware box:
     * sample rates of each analog input
     * how to intrepret the analog signals e.g. voltage based, resistance based and calibration e.g 2v-5v
     * labels for each analog input
     * sample rate of gps
     * sample rate of acclerometer
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
