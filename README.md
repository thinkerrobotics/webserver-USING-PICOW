
# webserver-USING-PICOW

This sketch will illustrate the basic operation of the WiFi library. It just connects the Pico to your local 2.4 GHz WiFi network and reads the IP address assigned to it by your network’s DHCP server.


## To download required files click on download buuton



[![MIT License](https://img.shields.io/badge/downloads-fdt?logo=%F0%9F%98%8A&label=code&labelColor=grey&color=green)](https://github.com/thinkerrobotics/webserver-USING-PICOW/archive/refs/heads/main.zip)



## code



```c++
/*
  Pi Pico W WiFi Station Demo
  picow-wifi-station.ino
  Use WiFi library to connect Pico W to WiFi in Station mode

  DroneBot Workshop 2022
  https://dronebotworkshop.com
*/

// Include the WiFi Library
#include <WiFi.h>

// Replace with your network credentials
const char* ssid = "YOUR_SSID";
const char* password = "YOUR_PASSWORD";

void setup() {

  // Start the Serial Monitor
  Serial.begin(115200);

  // Operate in WiFi Station mode
  WiFi.mode(WIFI_STA);

  // Start WiFi with supplied parameters
  WiFi.begin(ssid, password);

  // Print periods on monitor while establishing connection
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
    delay(500);
  }

  // Connection established
  Serial.println("");
  Serial.print("Pico W is connected to WiFi network ");
  Serial.println(WiFi.SSID());

  // Print IP Address
  Serial.print("Assigned IP Address: ");
  Serial.println(WiFi.localIP());

}

void loop() {

  delay(2000);

  // Print IP Address
  Serial.print("Assigned IP Address: ");
  Serial.println(WiFi.localIP());

}
```
## code explanation
We start, of course, by including the WiFi library.

Next, we define some character constants for the SSID and password for the network we wish to attach to. Of course, you’ll need to edit the code to match your network parameters.

In the Setup, we start the serial monitor, as we will use it to display our connection progress and our resulting IP address.

The next line specifies that we want to run in Station mode. This line is optional, if you omit it, the library will just default to station mode.

We then use a WiFi.begin to initiate the network connection. Note that we pass the SSID and password in this command.

We then wait for the network to connect by monitoring the status of the WL_CONNECTED constant. If it is FALSE, then we are not connected. While waiting, we print periods to the serial monitor as a progress indicator.

We then connect and print out the resulting IP address to the serial monitor.

In the Loop, we just repeat the IP address printout every two seconds. This is useful as you can’t have the serial monitor open while you upload to the Pico W, so by the time you get it open you may well miss the results from the Setup routine.

Load the sketch to your Pico W and observe the serial monitor. You should get an IP address indicating that you are connected to your network.


    
