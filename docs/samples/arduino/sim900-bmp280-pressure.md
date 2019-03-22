---
layout: docwithnav
title: Barometric pressure upload over HTTP using Arduino UNO, SIM900 Shield and BPM280 sensor
description: ThingsBoard IoT Platform sample for pressure data upload over HTTP using Arduino UNO, SIM900 GSM shield and BMP280 sensor.

---

* TOC
{:toc}

## Introduction

{% include templates/what-is-thingsboard.md %}

This sample application performs collection of pressure values produced by [BMP280 sensor](https://www.bosch-sensortec.com/bst/products/all_products/bmp280) and further visualization on the real-time web dashboard.
Collected data is pushed via HTTP to ThingsBoard server for storage and visualization.
The purpose of this application is to demonstrate ThingsBoard [data collection API](/docs/user-guide/telemetry/) and [visualization capabilities](/docs/user-guide/visualization/).

The BMP280 sensor is connected to [Arduino UNO](https://en.wikipedia.org/wiki/Arduino).
Arduino UNO connects to the Intenet using [SIM900 GSM shield](https://www.amazon.com/SIM900-GPRS-Shield-module-Board/dp/B00X378PNQ).
Arduino UNO pushes data to ThingsBoard server via HTTP protocol by using [Arduino ThingsBoard SDK](https://github.com/thingsboard/ThingsBoard-Arduino-MQTT-SDK).
Data is visualized using built-in customizable dashboard.
The application that is running on Arduino UNO is written using Arduino SDK which is quite simple and easy to understand.

Once you complete this sample/tutorial, you will see your sensor data on the following dashboard.

![image](http://via.placeholder.com/640x360)

{% include templates/prerequisites.md %}

## List of hardware

 - [Arduino UNO](https://store.arduino.cc/product/GBX00066)

   ![image](/images/samples/arduino/pressure/arduino-uno-pinout.png)

 - [BMP280 sensor](https://www.bosch-sensortec.com/bst/products/all_products/bmp280)

   ![image](/images/samples/arduino/pressure/bmp280-sensor.jpg)

 - [SIM900 GSM shield](https://makeradvisor.com/tools/sim900-gsm-gprs-shield/)

   ![image](/images/samples/arduino/pressure/gsm-shield.jpg)

## Wiring

### SIM900 shield connection

**TODO**
**TODO: describe issues with power**

### BMP280 connection

**TODO**

## Device provisioning

This step contains instructions that are necessary to connect your device to ThingsBoard.

Open ThingsBoard Web UI (http://localhost:8080) in browser and login as tenant administrator.
If you loaded the demo data during TB installation, the next credentials can be used:

 - login: tenant@thingsboard.org
 - password: tenant

Go to "Devices" section. Click "+" button and create a device with the name "Arduino UNO Demo Pressure Device". Set "Device type" to "default".

![image](http://via.placeholder.com/640x360)

Once device created, open its details and click "Manage credentials".

Copy auto-generated access token from the "Access token" field. Please save this device token. It will be referred to later as **$ACCESS_TOKEN**.

![image](http://via.placeholder.com/640x360)

## Provision your dashboard

Download the dashboard file using this [**TODO**]().
Use import/export [**instructions**](/docs/user-guide/ui/dashboards/#dashboard-importexport) to import the dashboard to your ThingsBoard instance.

## Creating Arduino firmware

If you already familiar with basics of Arduino UNO programming using Arduino IDE you can skip the following step and proceed with step 2.

### Step 1. Arduino UNO and Arduino IDE setup.
In order to start programming the Arduino UNO device, you will need Arduino IDE and all related software installed.

Download and install [Arduino IDE](https://www.arduino.cc/en/Main/Software).

To learn how to connect your Uno board to the computer and upload your first sketch please follow this [guide](https://www.arduino.cc/en/Guide/ArduinoUno).

### Step 2. Install Arduino ThingsBoard SDK and dependencies

To simplify application development, install the ThingsBoard Arduino SDK and its dependencies from standard Arduino library repository:

1. Proceed to **Sketch -> Include Library...** submenu. Select **Manage Libraries**.

1. Find and install **ThingsBoard Arduino SDK** and **PubSubClient by Nick O'Leary** libraries.

   ![image](http://via.placeholder.com/640x360)

1. Install **ArduinoJSON** library. <span style="color:red">Do not install beta releases of the ArduinoJson library. Instead, use **5.13.3** version of the library</span>, as shown in picture below.

   ![image](http://via.placeholder.com/640x360)

### Step 3. Install BMP280 library

**TODO**

### Step 4. Install SIM900 driver

**TODO**

### Step 5. Prepare and upload a sketch.

Download and open **arduino-bmp280-sim900-http.ino** sketch.

**Note** You need to edit following constants and variables in the sketch:

- `apn` - GPRS access point name. Consult your cellular network provider to get more information.
- `user` - GPRS access point user. Consult your cellular network provider to get more information.
- `pass` - GPRS access point password. Consult your cellular network provider to get more information.
- `TOKEN` - the **$ACCESS_TOKEN** from ThingsBoard configuration step.
- `THINGSBOARD_SERVER` - ThingsBoard HOST/IP address that is accessible from within your wifi network. Specify "demo.thingsboard.io" if you are using [live demo](https://demo.thingsboard.io/) server.
- `THINGSBOARD_PORT` - HTTP port to connect to. Change it if necessary.

**TODO**
* Add adruino sketch code here
**END OF TODO**

Connect your Arduino UNO device via USB cable and select "Arduino/Genuino Uno" port in Arduino IDE. Compile and Upload your sketch to the device using "Upload" button.

After application will be uploaded and started it will try to connect to ThingsBoard node using HTTP and upload "pressure" timeseries data once per second.

## Troubleshooting

When the application is running you can select "Arduino/Genuino Uno" port in Arduino IDE and open "Serial Monitor" in order to view debug information produced by serial output.

## Data visualization

Finally, open ThingsBoard Web UI. You can access this dashboard by logging in as a tenant administrator. Use

 - login: tenant@thingsboard.org
 - password: tenant

in case of local ThingsBoard installation.

Go to **"Devices"** section and locate **"Arduino UNO Demo Pressure Device"**, open device details and switch to **"Latest telemetry"** tab.
If all is configured correctly you should be able to see latest values of *"pressure"* in the table.

![image](http://via.placeholder.com/640x360)

After, open **"Dashboards"** section then locate and open **"Arduino BMP280: Pressure Demo Dashboard"**.
As a result, you will see two time-series charts and a digital gauge displaying pressure level (similar to dashboard image in the introduction).
