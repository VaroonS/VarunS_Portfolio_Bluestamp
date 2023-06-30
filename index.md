#  Dual Axis Solar Tracker 
The Dual Axis Solar Tracker is an arduino operated solar panel that is moved along a horizontal and vertical axis using servos. The tracker obtains inputs from a board that contains 4 photoresistors, obtaining light value inputs for each photoresistor, and computing these values to obtain two new values that correspond to angles that a vertical and horizontal servo need to rotate to. In completing this project, additional modifications have been implemented that utilizes a second sensor, this time for water level, and  using the inputs obtained from this sensor in order to let power run from the solar panel to a pump. The process of creating this tracker and the associated additional features is detailed in the document below.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Varun S | American High School| Power Production-Distribution-Management | Incoming Junior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone
My final milestone for this project was completed towards the conclusion of the third week of the program, and as such, the end of the program as well. My final working setup involves a solar panel that powers a small water pump , with the wires of the solar panel and the pump being partially connected (the ground wires were connected), while the other wires were attached to the relay, allowing me to control when a connection occured between the powersource wire and the wire that will require power. I am controlling this pump via a water sensor that will output a binary value that I can utilize in a conditional statement. The overall project heavily differs from my original plan to have a pump activate when the water level in a tank becoems too high, allowing for drainage, with the new project using an opposite concept, having a pump fill a separate container with water until a desired water level is reached. The reason for this shift is that when I pump water into a lower, separate container, my pump only needs to run for one or two seconds before it isn't required anymore, as gravity takes over the remainer of the job. I decided that pumping into a higher tank a specific amount of water would be far more technically challenging and would also be far more practical for a real world application where a fluid flow into a container might need to be controlled, and so only a specifc amount of fluid would need to be pumped. Throughout this process I have also had quite a few unresolved challenges that I will continue to work through eve when the program is over. One of these is my challenge with  the fact that none of the solar panels I had would  run my pump despite a clear voltage and current output on the multimeter. Another such challenge is that I have still been unable to wire my pump system simultaeneously with my arduino shield solar tracking system.  I have quite a few plans to resolve these issues and to continue to improve my project. Overall, I have been satisfied with the way my project has functioned, and I have accomplished most of the features I set out to conquer. 

# Second Milestone
My second milestone for this project was achieved towards the end of the second week of the program. At this point, I have succeeded in getting my water sensor to function as intended, outputting low values when the sensor is not submerged, and values near one thousand when the sensor is submerged. The entire process of wiring my water sensor was rather difficult, and it took some testing of various wire and sensor orientations in order to discover the root of problems I faced in obtaining the correct outputs. The sensor itself consists of a wired bulb that is capped with a diamond shaped structure that is to be submerged in fluid. 4 wires lead out from this into a small board, which are then consolidated into 3 wires that connect to the Arduino Board. After rewiring the circuits mutiple times, I came to the conclusion that the problem was related to the fact that the pins at the top of the shiled were connected to the transistors, which affected the inputs and outputs and prevented the setup from working as intended. Wiring the sensor to the board directly solved the issue, however I must now modify my shield so that I can wire the board underneath it. I hope to accomplish thsi by my final milestone, alongside my completed system. 

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**



# First Milestone
The first milestone for this project was completed between the first and second weeks of the program. I have currently managed to completely build a working solar tracker that successfully takes  light input via photoresistors and utilizes the code given by BrownDogGadgets to output light reading values for each of the photoresistors, average readings for each set of photoresistors (left, right, down, top), and of course, angles that the servos of the tracker need to orient the solar panel at an ideal angle. Regardless, a few challenges remain to be overcome, and modification is essential in the coming weeks. One such challenge that I have faced, and that which I am currently attempting to resolve, is the issue of the voltmeter that is directly connected to the solar panel, which has not been functional as of yet. Various steps to resolve this problem have been taken, including cutting the wires, re-stripping a small portion of the insulation, and then reconnecting the wires, however this has been to no avail. Another challenge I have been working through is wire management, and I hope to resolve this issue by the completion period of my second milestone. Additionally,  I aim to ameliorate the condition of my wire management such that the wires are not getting in the way of moving parts and are contained within the main frame of the solar tracker. All in all, I believe that the project has been set on a path to completion and successful modification, and it is indispensable that challenges be overcome by the conclusion of the second milestone.




**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**


# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Below is all the code I used in order to make this project run correctly. Due to limitations on wiring space due to the arduino shield, I have been pushed to run the Solar tracking element seperatley from the pumping element, and as such, I have two different code sections. The code below is my code for the pumping and water sensor mechanism. I would like to mention the official code provided by CQRobot, the manufacturer of the sensor, as I utilized a similar code structure to their.

```//Initialization
int SENSOR_PIN= A4;
int val;
int RELAY_PIN = A5;
void setup()
{ 
Serial.begin(9600);
//setting inputs and outputs:
pinMode(SENSOR_PIN,INPUT);
pinMode(RELAY_PIN, OUTPUT);
}
void loop()
{
val=digitalRead(SENSOR_PIN);// read sensor value 
Serial.println(val); // print the data from the sensor for debugging
delay(100);
//Conditional statements for pump activation
if(val==LOW)
{ digitalWrite(RELAY_PIN, LOW);}
else
{ digitalWrite(RELAY_PIN,HIGH);}

}

```
Additionally, here  is the code for the solar tracking mechanism, which is from BrownDogGadget's  official website for their Solar Tracker.

```/*
 * Dual_Axis_Tracker_V3.ino
 *
 * Brown Dog Gadgets <https://www.browndoggadgets.com/>
 * 
 */

// include Servo library
#include <Servo.h>

// horizontal servo
Servo horizontal;
int servoh = 90;

int servohLimitHigh = 180;
int servohLimitLow = 65;

Servo vertical;
int servov = 90;

int servovLimitHigh = 120;
int servovLimitLow = 15;


// LDR pin connections
int ldrTR = 0; // LDR top right
int ldrTL = 1; // LDR top left
int ldrBR = 2; // LDR bottom right
int ldrBL = 3; // LDR bottom left


void setup() {
  Serial.begin(9600);
  // servo connections
  horizontal.attach(5);
  vertical.attach(6);
  // move servos
  horizontal.write(90);
  vertical.write(45);
  delay(3000);
}


void loop() {

  int tr = analogRead(ldrTR); // top right
  int tl = analogRead(ldrTL); // top left
  int br = analogRead(ldrBR); // bottom right
  int bl = analogRead(ldrBL); // bottom left

  int dtime = 0; // change for debugging only
  int tol = 50;

  int avt = (tl + tr) / 2; // average value top
  int avd = (bl + br) / 2; // average value bottom
  int avl = (tl + bl) / 2; // average value left
  int avr = (tr + br) / 2; // average value right

  int dvert = avt - avd;  // check the difference of up and down
  int dhoriz = avl - avr; // check the difference of left and right


  // send data to the serial monitor if desired
  Serial.print(tl);
  Serial.print(" ");
  Serial.print(tr);
  Serial.print(" ");
  Serial.print(bl);
  Serial.print(" ");
  Serial.print(br);
  Serial.print("  ");
  Serial.print(avt);
  Serial.print(" ");
  Serial.print(avd);
  Serial.print(" ");
  Serial.print(avl);
  Serial.print(" ");
  Serial.print(avr);
  Serial.print("  ");
  Serial.print(dtime);
  Serial.print("   ");
  Serial.print(tol);
  Serial.print("  ");
  Serial.print(servov);
  Serial.print("   ");
  Serial.print(servoh);
  Serial.println(" ");


  // check if the difference is in the tolerance else change vertical angle
  if (-1 * tol > dvert || dvert > tol) {
   if (avt > avd) {
     servov = ++servov;
      if (servov > servovLimitHigh) {
        servov = servovLimitHigh;
      }
    }
    else if (avt < avd) {
      servov = --servov;
      if (servov < servovLimitLow) {
        servov = servovLimitLow;
      }
    }
    
    vertical.write(servov);
  }

  // check if the difference is in the tolerance else change horizontal angle
  if (-1 * tol > dhoriz || dhoriz > tol) {
    if (avl > avr) {
      servoh = --servoh;
      if (servoh < servohLimitLow) {
        servoh = servohLimitLow;
      }
    }
    else if (avl < avr) {
      servoh = ++servoh;
      if (servoh > servohLimitHigh) {
        servoh = servohLimitHigh;
      }
    }
    else if (avl = avr) {
      // nothing
    }
    
    horizontal.write(servoh);
  }
  
  delay(dtime);
  
}




```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|Arduino Relay|Used to control pump power flow|$5.89|https://tinyurl.com/3wkc9dp9|
|Battery Clip 9V with JACK connector|Connect 9V battery to board|$6.99 |https://tinyurl.com/449hjb8b|
|Dual Axis Solar Tracker Kit|Base Solar Tracker Build|$150.00|https://www.browndoggadgets.com/products/dual-axis-smart-solar-tracker|
|2x Duracell 9V batteries|Used to power board and test parts|$8.99|https://tinyurl.com/ymwhvf6u|
|Plusivo Soldering Iron Kit|Solder loose wire connections and provides othe materials|$24.99|https://tinyurl.com/4hccdk9a|



# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
