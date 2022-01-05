# M5Stack_Atom_Digole_Screen
A basic way of quickly integrating the M5Stack Atom to the Digole range of screens - using hardware serial via the Atom's grove port.

M5Stack offer a lot of modules with built in screens, but you may have one of their super-compact "Atom" ESP32 modules.                
These have several IO pin-holes, as well as a nice and tindy "grove" connector just above the USB-C port.            

This little project shows you what you need to edit in the Digole Arduino sketch to use the lightweight ESP32 hardware serial user-defined pins for the screen's UART mode.     
It also uses a grove breakout cable to show you how tidy the solution can be, no loose wires all over the place. =)

You'll need:          
1: An M5Stack Atom (Lite is ok).            
https://shop.m5stack.com/collections/atom-series/products/atom-lite-esp32-development-kit        
![image](https://user-images.githubusercontent.com/1586332/148209855-9209361b-70d9-4b48-b4d0-41f920e71d66.png)


2: A Digole screen:                 
https://www.digole.com/index.php?categoryID=153         
![image](https://user-images.githubusercontent.com/1586332/148209269-f9644801-c7a0-4c14-bc54-0027681b217d.png)


3: Grove 4 pin female jumper conversion cable.         
Mine was from here: https://www.ebay.co.uk/itm/131711076935               
![image](https://user-images.githubusercontent.com/1586332/148208869-bce4ecf1-9e92-4551-9d86-acf48cc585a0.png)


The result:       
![image](https://user-images.githubusercontent.com/1586332/148209590-dc1cbcf7-6690-4336-bb1b-702b736fb5dd.png)

The code's included in this project, there's only a few small changes needed to get hardware serial communication via the grove port.

The code change to the Digole example sketch: "_3D_Cube_Color.ino"                
The first thing to do is define the grove sockets pins (line 4 and 5), and initialise the second HardwareSerial port using the name OLEDSerial. (line 6)    
(There's three ports available: 0, 1 and 2.)          
Line 16 then declares the Digole screen as normal, but rather than the built in hardware Serial pins of an Arduino, we pass in the ESP32 hardware serial object. Using hardware serial is a tiny bit less CPU intensive than the software version.                     
![image](https://user-images.githubusercontent.com/1586332/148210515-035d6d6d-fbcd-4256-883a-7c6646324997.png)

Finally in Setup we initialise the hardware serial adapter, and pass in the receive and transmit pins we are using - the Grove port.              
![image](https://user-images.githubusercontent.com/1586332/148210653-c19c5b4f-87b0-4519-8a58-3e75f4ccbf55.png)

That should be it.
