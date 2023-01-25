---
layout: post
title: Flutter + ESP32 = Room temperature checker!
---

Ok, but what is this project?

Our project aims to design a simple system for temperature measurement and reading, which is practically applicable in every home. The system allows you to read the temperature from the rooms of the house using a transparent phone application. The main assumption of our system is to signal an alarm via SFM-27-11 when the temperature exceeds 30 degrees.

The ESP32-DevKit WiFi module is responsible for processing sensor data for temperature control and the ability to send them to the server using a WiFi internet connection and saving them on the firebase server

Using the application on the phone, you can easily check the temperature in room.

ESP-32 Connection diagram
![_config.yml]({{ site.baseurl }}/images/esp-post/esp-connection-diagram.png)

Programming module - Client Firebase ESP-32

The Main think is to install a library supporting the firebase client on our ESP-32 module.

Next we need to program module ESP-32 to be able to send data to firebase server.

![_config.yml]({{ site.baseurl }}/images/esp-post/esp-firebase-client.png)

In the attached image, we can see the code connecting to serial communication.
Then tried to connect to the router and firebase client. If everything goes well, we manage to communicate with the firebase database. All messages will be displayed on the console.

The problem we encountered with the analog temperature reading. The ESP-32 has DIGITAL pins. So using the analog to digital (ADC ) function and the reference temperature.

![_config.yml]({{ site.baseurl }}/images/esp-post/esp-analog-to-digital.png)

We used the readADC_cal function to replace the value read from the PIN-out

![_config.yml]({{ site.baseurl }}/images/esp-post/esp-convert-to-temp.png)

Which converts the appropriate value to Temperature.

To manage the buzzer, we used the EasyBuzzer library, after reaching a temperature greater than 30 degrees, the buzzer automatically turns on, signaling an alarm that the temperature is too high.

![_config.yml]({{ site.baseurl }}/images/esp-post/esp-buzzer.png)

Each data which will read from ESP-32 module will save on Firebase Realtime DataBase.


![_config.yml]({{ site.baseurl }}/images/esp-post/esp-firebase-temp.png)

To read data from the server i implemented simple flutter app:

![_config.yml]({{ site.baseurl }}/images/esp-post/esp-mobile.gif)
