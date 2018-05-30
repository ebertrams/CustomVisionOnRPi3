# Custom Vision + Azure IoT Edge on a Raspberry Pi 3 demo

This is a sample showing how to deploy a Custom Vision model to a Raspberry Pi 3 device running Azure IoT Edge. This solution is made of 3 modules:

- **Camera capture** - this module captures the video stream from a USB camera, sends the frames for analysis to the custom vision module and shares the output of this analysis to the edgeHub. This module is written in python and uses [OpenCV](https://opencv.org/) to read the video feed.
- **Custom vision** - it is a web service over HTTP running locally that takes in images and classifies them based on a custom model built via the [Custom Vision website](https://azure.microsoft.com/en-us/services/cognitive-services/custom-vision-service/). This module has been exported from the Custom Vision website and slightly modified to run on a ARM architecture. You can modify it by updating the model.pb and label.txt files to update the model.
- **SenseHat display** - this module gets messages from the edgeHub and blinks the raspberry Pi's senseHat according to the tags specified in the inputs messages. This module is written in python and requires a [SenseHat](https://www.raspberrypi.org/products/sense-hat/) to work.

## Get started
Build the full solution by running the `Build IoT Edge Solution` command from the [Azure IoT Edge extension in VS Code](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.azure-iot-edge).