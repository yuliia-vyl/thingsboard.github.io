---
layout: docwithnav
title: ESP32 Pico Kit GPIO control and DHT22 sensor monitor using ThingsBoard Arduino SDK
description: ThingsBoard IoT Platform sample for ESP32 Pico Kit GPIO control and temperature/humidity monitor using ThingsBoard Arduino SDK 

---

* TOC
{:toc}

## Introduction

{% include templates/what-is-thingsboard.md %}

[ESP32](https://www.espressif.com/en/products/hardware/esp32/overview) is a series of low-cost, low-power system-on-a-chip microcontrollers with integrated self-contained Wi-Fi and dual-mode Bluetooth. ESP32 is a successor of ESP8266 chip.

This sample application will allow you to control GPIO of your ESP32 device using ThingsBoard web UI and display humidity/temperature data from DHT22 sensor. We will observe GPIO control using LEDs connected to the pins. The purpose of this application is to demonstrate ThingsBoard [RPC capabilities](/docs/user-guide/rpc/) and .

The application that is running on ESP32 is written using ThingsBoard Arduino SDK which is quite simple and easy to understand.

Current GPIO state and GPIO control widget is visualized using built-in customizable dashboard. 

## List of hardware

 - [ESP32 Pico Kit board](https://www.espressif.com/en/products/hardware/development-boards).

  ![image](https://docs.espressif.com/projects/esp-idf/en/latest/_images/esp32-pico-kit-v4.1-layout.jpg)

 - [DHT22 sensor](https://www.aliexpress.com/item/1pcs-DHT22-digital-temperature-and-humidity-sensor-Temperature-and-humidity-module-AM2302-replace-SHT11-SHT15/32316036161.html?spm=2114.03010208.3.49.aZvfaG&ws_ab_test=searchweb0_0,searchweb201602_2_10065_10068_10084_10083_10080_10082_10081_10060_10061_10062_10056_10055_10054_10059_10099_10078_10079_10093_426_10073_10103_10102_10096_10052_10050_10051,searchweb201603_6&btsid=28d9ee9a-283a-4e97-af7b-a7e530490916)

  ![image](/images/samples/arduino/temperature/dht22-pinout.png)

 - 6 LEDs
 - 6 Resistors in range between 68Ω and 100Ω
 - Breadboard
 - Micro-USB cable

## Wiring

### DHT22 connection

Pin | Connect to
-----------|-----------
DHT22 VCC |  Pico 5V
DHT22 DATA | Pico 33
 
### LEDs connection

Pin | Connect to
-----------|-----------
LED1 Anode | Pico 32 trough resistor (68Ω - 100Ω)
LED2 Anode | Pico 26 trough resistor (68Ω - 100Ω)
LED3 Anode | Pico 25 trough resistor (68Ω - 100Ω)
LED4 Anode | Pico 19 trough resistor (68Ω - 100Ω)
LED5 Anode | Pico 22 trough resistor (68Ω - 100Ω)
LED6 Anode | Pico 21 trough resistor (68Ω - 100Ω)
All LEDs cathodes | Pico Ground

### Connection diagram

The following picture summarizes the connections for this project:

![image](/images/samples/esp32/gpio-temperature/wiring.png)

## Device provisioning

This step contains instructions that are necessary to connect your device to ThingsBoard.

Open ThingsBoard Web UI (http://localhost:8080) in browser and login as tenant administrator

 - login: tenant@thingsboard.org
 - password: tenant
 
Go to "Devices" section. Click "+" button and create a device with the name "ESP32 Pico Device". Set "Device type" to "default". 

![image](/images/samples/esp32/gpio-temperature/device.png)

Once device created, open its details and click "Manage credentials".

Copy auto-generated access token from the "Access token" field. Please save this device token. It will be referred to later as **$ACCESS_TOKEN**.

![image](/images/samples/esp32/gpio-temperature/credentials.png)

## Provision your dashboard

Download the dashboard file using this [**link**](/docs/samples/esp32/resources/esp32_dht22_temp_and_gpio_dashboard.json). 
Use import/export [**instructions**](/docs/user-guide/ui/dashboards/#dashboard-importexport) to import the dashboard to your ThingsBoard instance.

## Creating ESP32 firmware

Easiest way to program ESP32 Pico Kit is to use Arduino IDE. Following sectoins are describing that approach. 

### ESP32 and Arduino IDE setup

First you will need Arduino IDE and all related software installed. 

Download and install [Arduino IDE](https://www.arduino.cc/en/Main/Software).

The Pico board support must be added to Arduino IDE before any program can be built and flashed into ESP32. To do so, install ESP32 package as described below:

1. Open Aduino IDE.

1. Open "File" menu, select "Preferences", and add a board manager URLs
   
   ```
   https://dl.espressif.com/dl/package_esp32_index.json,http://arduino.esp8266.com/stable/package_esp8266com_index.json
   ```

   into "Additional Boards Manager URL" field, as shown below:

   ![image](/images/samples/esp32/gpio-temperature/add-esp32-url.png)

1. In "Tools" menu, select "Board...". In a top of the list, select "Board manager".

1. Enter "ESP32" in the search field. Click "Install"

   ![image](/images/samples/esp32/gpio-temperature/install-esp32-arduino.png)

### Install Arduino ThingsBoard SDK

To simplify application development, install the ThingsBoard Arduino SDK from standart Arduino library repository:

1. Click on "Sketch" menu. Open "Include Library..." submenu. Select "Manage Libraries".

1. Type "ThingsBoard" in the search field.

1. Click install on "ThingsBoard Arduino SDK" library.

From now on, you can use ThingsBoard SDK right from Arduino IDE.

### Install ESP32 DHT22 driver

### Connect ESP32 Pico to PC

### Prepare and upload sketch

## Troubleshooting

## Data visualization

## See also

Browse other [samples](/docs/samples) or explore guides related to main ThingsBoard features:

 - [Device attributes](/docs/user-guide/attributes/) - how to use device attributes.
 - [Telemetry data collection](/docs/user-guide/telemetry/) - how to collect telemetry data.
 - [Using RPC capabilities](/docs/user-guide/rpc/) - how to send commands to/from devices.
 - [Rule Engine](/docs/user-guide/rule-engine/) - how to use rule engine to analyze data from devices.
 - [Data Visualization](/docs/user-guide/visualization/) - how to visualize collected data.

{% include templates/feedback.md %}
 
{% include socials.html %}

## Next steps

{% assign currentGuide = "HardwareSamples" %}{% include templates/guides-banner.md %}
