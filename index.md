#  Dual Axis Solar Tracker 
The Dual Axis Solar Tracker is an Arduino operated solar panel that is moved along a horizontal and vertical axis using servos. The tracker functions by obtaining inputs from a board that contains 4 photoresistors and computing these values to obtain two new values that correspond to angles that a vertical and horizontal servo need to rotate to. In completing this project, additional modifications have been implemented that utilizes a second sensor, this time for water level, and  using the inputs obtained from this sensor in order to let power run from the solar panel to a pump. The ultimate motivation for the creation of such a project is to utilize a reneweable energy source to accomplish a mechanical task. Pump systems are incredibly useful and are required for a wide array of  functions, including irrigation, hydropower, pools, and hydroelectric storage, and the concept this project seeks to provide a concept for using sensors to remotley control a water pump, perhaps to fil up a tank to a certain level, or to  allow a pool to drain after water reaches a threshold. The process of creating this tracker and the associated additional features are detailed in the document below.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Varun S | American High School| Power Production-Distribution-Management | Incoming Junior



![Headstone Image](logo.svg)
  
# Final Milestone
My final milestone for this project was completed towards the conclusion of the third week of the program. My final working setup involves a solar panel that powers a small water pump , with the wires of the solar panel and the pump being partially connected (the ground wires were connected), while the other wires were attached to the relay, allowing me to control when a connection occured between the powersource wire and the wire that will require power. I am controlling this pump via a water sensor that will output a binary value that I can utilize in a conditional statement.

![Insert Picture(s) of relay and all the wiring ]()

The overall project heavily differs from my original plan to have a pump activate when the water level in a tank becoems too high, allowing for drainage, with the new project using an opposite concept, having a pump fill a separate container with water until a desired water level is reached. The reason for this shift is that when I pump water into a lower, separate container, my pump only needs to run for one or two seconds before it isn't required anymore, as gravity takes over the remainer of the job. I decided that pumping into a higher tank a specific amount of water would be far more technically challenging and would also be far more practical for a real world application where a fluid flow into a container might need to be controlled, and so only a specifc amount of fluid would need to be pumped. Throughout this process I have also had quite a few unresolved challenges that I will continue to work through eve when the program is over. One of these is my challenge with  the fact that none of the solar panels I had would  run my pump despite a clear voltage and current output on the multimeter. 

![Insert Picture(s) of pump setup ]()


Another such challenge is that I have still been unable to wire my pump system simultaeneously with my arduino shield solar tracking system.  I have quite a few plans to resolve these issues and to continue to improve my project. Overall, I have been satisfied with the way my project has functioned, and I have accomplished most of the features I set out to conquer. 

# Second Milestone
My second milestone for this project was achieved towards the end of the second week of the program. At this point, I have succeeded in getting my water sensor to function as intended, outputting low values when the sensor is not submerged, and values near one thousand when the sensor is submerged. The entire process of wiring my water sensor was rather difficult, and it took some testing of various wire and sensor orientations in order to discover the root of problems I faced in obtaining the correct outputs. The sensor itself consists of a wired bulb that is capped with a diamond shaped structure that is to be submerged in fluid. 4 wires lead out from this into a small board, which are then consolidated into 3 wires that connect to the Arduino Board.

![Insert Picture(s) of sensor wiring ]()  

After rewiring the circuits mutiple times, I came to the conclusion that the problem was related to the fact that the pins at the top of the shiled were connected to the transistors, which affected the inputs and outputs and prevented the setup from working as intended. Wiring the sensor to the board directly solved the issue, however I must now modify my shield so that I can wire the board underneath it. I hope to accomplish thsi by my final milestone, alongside my completed system. 




<iframe width="560" height="315" src="https://www.youtube.com/embed/-O5K9Qy7PYQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe> 

# First Milestone
The first milestone for this project was completed between the first and second weeks of the program. I have currently managed to completely build a working solar tracker that successfully takes  light input via photoresistors and utilizes code to output light reading values for each of the photoresistors, average readings for each set of photoresistors (left, right, down, top), and of course, angles that the servos of the tracker need to orient the solar panel at an ideal angle. Regardless, a few challenges remain to be overcome, and modification is essential in the coming weeks. One such challenge that I have faced, and that which I am currently attempting to resolve, is the issue of the voltmeter that is directly connected to the solar panel, which has not been functional as of yet. Various steps to resolve this problem have been taken, including cutting the wires, re-stripping a small portion of the insulation, and then reconnecting the wires, however this has been to no avail. Another challenge I have been working through is wire management, and I hope to resolve this issue by the completion period of my second milestone. Additionally,  I aim to ameliorate the condition of my wire management such that the wires are not getting in the way of moving parts and are contained within the main frame of the solar tracker. All in all, I believe that the project has been set on a path to completion and successful modification, and it is indispensable that challenges be overcome by the conclusion of the second milestone.




<div style="position:relative;width:fit-content;height:fit-content;">
            <a style="position:absolute;top:20px;right:1rem;opacity:0.8;" href="https://clipchamp.com/watch/PNsgqw2mEzI?utm_source=embed&utm_medium=embed&utm_campaign=watch">
                <img loading="lazy" style="height:22px;" src="https://clipchamp.com/e.svg" alt="Made with Clipchamp" />
            </a>
            <iframe allow="autoplay;" allowfullscreen style="border:none" src="https://clipchamp.com/watch/PNsgqw2mEzI/embed" width="640" height="360"></iframe>
        </div>


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
Additionally, here  is the code for the solar tracking mechanism. The servos are initially set to  90 degrees before tracking begins, at which point photoresistor values are computed.

```
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

The first list below includes all components utilized in the completion of the project. This list does not include tools that will be neccesary in assembling various parts.

| **Component** | **Information** | **Expenses** | **Purchase Link** |
| ---      | ---      | ---       |---       |
|Arduino Relay|Used to control pump power flow|$5.89|<a href="https://tinyurl.com/3wkc9dp9">  Relay Link </a> |
|2x Arduino UNO Board| Second board used to run solartracking side by side with water sensing| $28.50| <a href="https://tinyurl.com/2fj7ea2s">  UNO board link </a> |
|1x Arduino Shield| Mounted on UNO board to use solar tracking feature. Shield design may vary | $10.39 | <a href="https://www.amazon.com/dp/B0832Z6W54/ref=sspa_dk_detail_2?psc=1&pd_rd_i=B0832Z6W54&pd_rd_w=DvVB7&content-id=amzn1.sym.eb7c1ac5-7c51-4df5-ba34-ca810f1f119a&pf_rd_p=eb7c1ac5-7c51-4df5-ba34-ca810f1f119a&pf_rd_r=N1SJM7YSBKRV1H6HE7VF&pd_rd_wg=2EOeo&pd_rd_r=4ac6ed04-3613-4d4a-81ed-c3a6e0ee8243&s=industrial&sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWw"> Arduino Shield  </a> |
|Battery Clip 9V with JACK connector|Connect 9V battery to board|$6.99 |<a href="https://tinyurl.com/449hjb8b"> 9V Battery link </a>|
|CQR Robot Contact Water Sensor|Wire  CQR board with 3.3 V, GND, and any digital pin on Arduino UNO board|$15.99|<a href="https://tinyurl.com/5bsmrxd9"> Sensor link </a>| 
|DC 3V 5V Micro Submersible Mini Water Pump | Connected with Relay and Power source to control via Arduino Board | $11.39 |<a href=" https://tinyurl.com/usdts5sw"> Pump link </a> |
|2x Duracell 9V batteries|Used to power board and test parts|$8.99|<a href="https://tinyurl.com/ymwhvf6u"> Battery link </a>|
|4x Photoresistors | Note: You will need to wire this into a small board before use. Brown Dog Gadgets provides a premade photoresistor board | $1.10 |<a href="https://www.walmart.com/ip/30x-Photoresistor-LDR-CDS-5mm-Light-Dependent-Resistor-Sensor-GL5516-Arduino-WL/2164396923?wmlspartner=wlpa&selectedSellerId=101243139"> Photoresistor Link </a>|
|Small 5-6V Solar Panel | Provides Solar Power | $6.99 |<a href="https://www.amazon.com/Sunnytech-100ma-Module-Polysilicon-Charger/dp/B008J9BZIA/ref=asc_df_B008J9BZIA/?tag=hyprod-20&linkCode=df0&hvadid=167157220945&hvpos=&hvnetw=g&hvrand=1605397731904216138&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9032047&hvtargid=pla-375588486157&psc=1"> Panel link </a>|
|2x Servos | Used to operate tracker | $3.78| <a href="https://www.amazon.com/Smraza-Helicopter-Airplane-Control-Arduino/dp/B07L2SF3R4/ref=sxin_16_pa_sp_search_thematic_sspa?content-id=amzn1.sym.1c86ab1a-a73c-4131-85f1-15bd92ae152d%3Aamzn1.sym.1c86ab1a-a73c-4131-85f1-15bd92ae152d&crid=3NP28RPJN3EST&cv_ct_cx=servos%2Bfor%2Barduino&keywords=servos%2Bfor%2Barduino&pd_rd_i=B07L2SF3R4&pd_rd_r=2ecb3d8e-a475-44d7-a7ce-442572954056&pd_rd_w=vlNQ8&pd_rd_wg=ljOeo&pf_rd_p=1c86ab1a-a73c-4131-85f1-15bd92ae152d&pf_rd_r=6GT8CGC726FEK676CER4&qid=1690920280&s=industrial&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sprefix=servos%2Bfor%2Barduino%2Cindustrial%2C253&sr=1-3-364cf978-ce2a-480a-9bb0-bdb96faa0f61-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&smid=AMIHZKLK542FQ&th=1"> Servo link </a>|
| | **NOTE:Expenses do not account for building materials for the frame of the tracker. Prices are estimates and some components will have to be purchased in bulk**| |**Total Sum of expenses: $100.00**|

The list below includes tools that were purchased for the completion of the project or that are highly reccomended.
| **Tool** | **Information** | **Expenses** | **Purchase Link** |
|--- | --- | --- | --- |
|Plusivo Soldering Iron Kit|Solder loose wire connections and provides othe materials| $24.99 |<a href="https://tinyurl.com/4hccdk9a"> Soldering Kit Link </a>|
|Klien Adjustable Screwdriver ID: 32314| Provides a wide array of screw types and sizes.| $19.30 | <a href="https://www.walmart.com/ip/Klein-Tools-32314-14-in-1-Precision-Screwdriver-Nut-Driver/579787783"> Screwdriver link </a>|
|Wire Stripper| Extensively used in adjusting wire length and stripping wires | $7.39 | <a href="https://tinyurl.com/hbh4965v"> Wire stripper link </a>| |

Additional tools that were used include a power screw driver with a 3/4th to 5/8th inch flat drill bit. These are not absolutely neccesary, however, they may be prefered for a more compact and well managed build. 


# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
