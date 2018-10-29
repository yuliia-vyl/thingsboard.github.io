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
 - 6 Resistors
 - Breadboard
 - Micro-USB cable

## Connection diagram

## Device provisioning

## Dashboard creation

## Creating ESP32 firmware

### ESP32 and Arduino IDE setup

### Install Arduino ThingsBoard SDK

### Install ESP32 DHT22 driver

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
