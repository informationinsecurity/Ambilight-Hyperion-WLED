# Ambilight-Hyperion-WLED
This is a set of instructions on how to make a DIY ambilight configuration with an rPi, ESP8266 and individually addressable LED strip

# Parts List

	•	HDMI -> USB capture card - https://www.amazon.com/gp/product/B08G4T1NDJ/

 	•	Led strip angle connectors - https://www.amazon.com/gp/product/B087Q7QYMG/

  	•	4K hdmi splitter (1 4k 1 1080p)- https://www.amazon.com/gp/product/B07DQBY5TX/

  	•	Individually addressable LED strip (WS2812B)-https://www.amazon.com/gp/product/B07FVP54GQ/

  	•	LED Strip power supply (5v)- https://www.amazon.com/gp/product/B082D97W98/

  	•	ESP8266 NodeMCU microcontroller - https://www.amazon.com/gp/product/B081CSJV2V/

  	•	Misc items – 2 HDMI cables, microusb cable, wires, soldering iron

# Instructions 

1.	Flash ESP8266 with WLED -  Follow this blog post to get WLED configured and running (no wiring of LEDs yet) - https://tynick.com/blog/11-03-2019/getting-started-with-wled-on-esp8266/

2.	Wire the LED strip to the ESP8266 and test WLED to confirm it works
	
	a.	Power wire (Red) from LED goes to VIN on ESP8266
	
	b.	Ground wire (Black) from LED goes to GND on ESP8266
	
	c.	Data wire (Green) goes to D4 on ESP8266
	
3.	Setup Raspberry pi on Raspbian (or any other linux OS)

4.	Install Hyperion NG on Pi - https://github.com/hyperion-project/hyperion.ng/releases

5.	Wire up all the components- 
	a.	Input Device (Apple TV in my case -> HDMI Splitter –> one end to tv, other to capture device hdmi -> capture device USB plugged into pi
	
6.	Browse to Hyperion webserver (http://\<ip>:8090)

7.	Select LED Hardware Tab

	a.	Controller type: wled
	
	b.	RGB byte order: RGB
	
	c.	Target IP / Hostname:  \<ip address of WLED controller>
	
8.	Select LED Layout Tab

	a.	Configure this as needed. My settings for my 60in TV are:
	
		i.	Top and Bottom – 40 LEDs
	
		ii.	Sides – 22 LEDs
	
		iii.	Set input position to where you are starting your leds from. The flow should match your wiring
	
9.	Select Capturing Hardware
	a.	Enable the option “Enable USB Capture”
	
	b.	For USB Capture settings I use the following (they may need tweaking)
	
		i.	Device- USB Video
		
		ii.	Video Standard NTSC
		
		iii.	Device Resolution 640x480
		
		iv.	20 FPS
		
		v.	Size Decimation 3	
		
	c.	Save configuration
	
10.	To test everything:

	a.	Video Capture – In Hyperion top right menu, select the “TV icon” and enable “live video”. This should display the current picture from the TV.
	
	b.	WLED- When you open WLED via the app, the light should say “(Live)” next to it – this means it’s talking to hyperion and waiting for instructions
	
11.	Once the lights and Hyperion seem to be working properly, this is when I measure and cut my LED strips and use the angle connectors.

12.	Tape or Velcro the cut strips of LED to the TV and ensure the wiring is proper (Make sure to note the arrows for data flow on the strip and do not reverse polarity!

