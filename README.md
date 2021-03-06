# LEDMatrix
The instructions for replicating the hardware for this project can be found on https://www.hackster.io/windows-iot/led-matrix-c00e39

## Universal Windows Platform
The "big brain" component of this project can run on any device that supports the Universal Windows Platform.  It has been tested on Windows Phone 10 and Windows 10 Desktop.
## Arduino
The "little brain" component of this project runs on an Arduino, and needs to have a sketch loaded to support the kind of LED hardware you're running.  Included implementations are:
- LedCurtainFirmata - This is the configuration that was shown at //build 2015, at Maker Faire San Mateo and Maker Faire Shenzhen, and is documented in the Hackster post.  The LED "Curtain" is made up of strips of LPD8806-based RGB LEDs, cut into 48 strips of 48 "pixels" each (2304 total pixels).  They are connected into one long serial string, with pixel "zero" starting in the bottom left hand corner of the screen. This is the sketch that should be used, as it is configured to run with the UWP.
- LedCurtainUsbFirmata - Uses the internal/USB serial interface on a Leonardo (Serial instead of Serial1) instead of the externally exposed serial.  This can be used for directly connecting the curtain to a desktop or IoTCore device, rather than going over BlueTooth from a Windows Phone.
- LedMatrixPanelFirmata - This sketch is a rework of the code in order to drive a 32x32 LED Matrix panel from Adafruit. To use this code, this "MainPage.Xaml.Cs" file in the UWP will need to instantiate a "LedMatrixPanel" object with a 32 width and 32 height, instead of the default Lpd8806Matrix. It is important to note that driving this LED panel requires the Arduino to load the entire frame's worth of color values into memory, so its a much more major draw on the Arduino's resources.
