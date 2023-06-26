 #  Dual Axis Solar Tracker 
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Varun S | American High School| Power Production-Distribution-Management | Incoming Junior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone


**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Second Milestone
My second milestone for this project was achieved on the 22nd of June, 2023. At this point, I have succeeded in getting my water sensor to function as intended, outputting low values when the sensor is not submerged, and values near one thousand when the sensor is submerged. The entire process of wiring my water sensor was rather difficult, and it took some testing of various wire and sensor orientations in order to discover the root of problems I faced in obtaining the correct outputs. The sensor itself consists of a wired bulb that is capped with a diamond shaped structure that is to be submerged in fluid. 4 wires lead out from this into a small board, which are then consolidated into 3 wires that connect to the Arduino Board. After rewiring the circuits mutiple times, I came to the conclusion that the problem was related to the fact that the pins at the top of the shiled were connected to the transistors, which affected the inputs and outputs and prevented the setup from working as intended. Wiring the sensor to the board directly solved the issue, however I must now modify my shield so that I can wire the board underneath it. I hope to accomplish thsi by my final milestone, alongside my completed system. 

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# First Milestone
The first milestone for this project was completed on the 16th of June, 2023. I have currently managed to completely build a working solar tracker that successfully takes  light input via photoresistors and utilizes the code given by BrownDogGadgets to output light reading values for each of the photoresistors, average readings for each set of photoresistors (left, right, down, top), and of course, angles that the servos of the tracker need to orient the solar panel at an ideal angle. Regardless, a few challenges remain to be overcome, and modification is essential in the coming weeks. One such challenge that I have faced, and that which I am currently attempting to resolve, is the issue of the voltmeter that is directly connected to the solar panel, which has not been functional as of yet. Various steps to resolve this problem have been taken, including cutting the wires, re-stripping a small portion of the insulation, and then reconnecting the wires, however this has been to no avail. One way in which this problem was tested was by connecting the solar panel to a different voltmeter that was known to be functional, and by doing this, I was able to conclude the problem was related to the voltmeter, given that an output from the panel was detected, and hence, I simply decided to abandon using the voltmeter as I anyways intend to wire my panel to a different system.  Another challenge I have been working through is wire management, and I hope to resolve this issue by the completion period of my second milestone. Additionally,  I aim to ameliorate the condition of my wire management such that the wires are not getting in the way of moving parts and are contained within the main frame of the solar tracker. All in all, I believe that the project has been set on a path to completion and successful modification, and it is indispensable that challenges be overcome by the conclusion of the second milestone.




**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
|:--:|:--:|:--:|:--:|

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
