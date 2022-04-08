# nodeMCU_wifi_jamming
 
NodeMCU based Wi-Fi jamming system (IOT PROJECT)
Name: Mutahara Ghulam Rasool                                                                                                             Reg: BSCS2019-14
 
 
                              (Report)



1.	Introduction:
we will make "WiFi Deauther" using NodeMCU ESP8266. This software allows you to perform a deauth attack with an ESP8266 against selected networks. The deauth attack will, if the connection is vulnerable, disconnect the devices from the network. Because the attack is running constantly, the devices will be disconnected again and again. Depending on the network, that can either block a connection or slow it down.
2.	Software required:
•	Driver:
	https://github.com/HobbyComponents/CH...	
•	Ardinuo IDE:
	https://www.arduino.cc/en/software
•	Esp8266 DE authorized module:
	https://github.com/Anuarul/esp8266_deauther-master.git
3.	Hardware required:
•	NodeMCU ESP8266 WiFi
•	Data cable:

4.	Compilation:
Download the source code of this project.
	1 Install Arduino and open it.
	2 Go to File > Preferences
	3 Add http://arduino.esp8266.com/stable/package_esp8266com_index.json to the Additional Boards Manager URLs. 
 
	4 Go to Tools > Board > Boards Manager
	5 Type in esp8266
	6 Select version 2.0.0 and click on Install (must be version 2.0.0!)
 
Go to File > Preferences
	8 Open the folder path 
	9 Go to packages > esp8266 > hardware > esp8266 > 2.0.0 > tools > sdk > include
	10 Open user_interface.h with a text editor
	11 Scroll down and before #endif add following lines:
                       typedef void (*freedom_outside_cb_t)(uint8 status);
                       int wifi_register_send_pkt_freedom_cb(freedom_outside_cb_t cb);
                       void wifi_unregister_send_pkt_freedom_cb(void);
                       int wifi_send_pkt_freedom(uint8 *buf, int len, bool sys_seq);
 


Go to the SDK_fix folder of this project
	13 Copy ESP8266Wi-Fi.cpp and ESP8266Wi-Fi.h
	14 Paste these files here packages > esp8266 > hardware > esp8266 > 2.0.0 > libraries > ESP8266WiFi > src
	15 Open esp8266_deauther > esp8266_deauther.ino in Arduino
	16 Select your ESP8266 board at Tools > Board and the right port at Tools > Port
If no port shows up you may have to reinstall the drivers.
	17 Depending on your board you may have to adjust the Tools > Board > Flash Frequency and the Tools > Board > Flash Size. I use a 160MHz flash frequency and a 4M (3M SPIFFS) flash size.
	18 Upload!
Your ESP8266 Deauther is now ready!
5.	How does it work?
First start your ESP8266 by plugging it in and giving it power.
Scan for Wi-Fi networks and connect to pwned. The password is deauther.
Once connected, you can open up your browser and go to 192.168.4.1.
 
You can now scan for networks...
 



 

 



 



 
