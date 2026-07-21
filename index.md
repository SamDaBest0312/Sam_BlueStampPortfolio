# Hexapod
The Hexapod is a six-legged programmable robot inspired by insect movement. It has a durable acrylic body, with each leg powered by three servo motors for precise motion. Controlled by an Arduino board, it can be operated wirelessly using a smartphone, computer, or an Arduino-based controller. The Hexapod is designed for customization and provides a hands-on way to learn robotics and engineering.


You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Sam S | Valley Christian | Electrical Engineering | Incoming Sophomore

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone
**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/4XMwXY6aMnE?si=J0ydwP5090QXWsCZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone

Since my first milestone, I have assembled and programmed my Hexapod's wireless controller. The controller is built using custom parts, an acrylic plate, a joystick, a 9V battery, and a wireless transmitter. A matching transmitter is installed on the Hexapod, allowing the controller and robot to communicate wirelessly. This is an important step because it will allow me to control the robot's movements during Demo Night.

One thing that has surprised me is how even the smallest mistakes can have a huge impact on the project. While programming the controller, I accidentally entered the robot's address as **0X** instead of **0x**. Since Arduino requires the lowercase **x** for hexadecimal values, the controller could not connect to my robot. Although the mistake was small, it took careful troubleshooting to identify and fix.

The biggest challenge I overcame during this milestone was learning to use the Arduino IDE and understanding how to program the controller so it communicated specifically with my Hexapod. Through trial and error, I became much more confident in both programming and debugging.

Before my final milestone, I still need to build a secure battery holder for the robot, make a few final modifications, and thoroughly test the Hexapod to ensure it is ready to be demonstrated successfully at Demo Night.

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/V3EhGzdjBcM?si=831zDcTtIsLLuKjw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


My project is the Hexapod, a six-legged robot that combines mechanical design, electronics, and programming. I chose this project because it gives me the chance to learn many different engineering skills while building something challenging. The Hexapod is made of acrylic parts, 18 servos, a 7.2V battery, a breadboard, and other electronic components that all work together to control its movement.

So far, I have completed the main body and attached all six legs. Every servo is connected to a specific port, and I have organized the wiring using cable ties to keep everything neat and reliable. I also soldered the battery connector and power wires so the battery can safely supply power to all 18 servos at the same time.

One of the biggest challenges I faced was aligning the servos correctly. While assembling the body, I discovered that one servo was misaligned, and while trying to fix it, I accidentally damaged several servos and other parts. Since every servo controls a different movement, this prevented the Hexapod from functioning properly. With guidance from my mentors and careful troubleshooting, I was able to replace the damaged parts and continue building.

For my next milestones, I plan to connect the controller, program the Hexapod's movements, and test its walking abilities. My goal is to have a fully functional robot that I can demonstrate at Demo Night while gaining a deeper understanding of robotics and engineering throughout the process.

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
| Calibration Graph | Brain of the Hexapod | Only sold with Hexapod | <a href="[https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1]"> Link </a> |
| Acrylic Parts (Robot and Remote set | Structure and main parts of the Hexapod | Only sold with Hexapod | <a href="[https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1]"> Link </a> |
| Servos (18) | Rotation and movement of the Hexapod limbs | $17 | <a href="[https://www.amazon.com/Hosyond-MG996R-Digital-Motors-Helicopter/dp/B0BYD9M1P3/ref=sr_1_17_sspa?crid=3TW5W06Y90D49&keywords=arduino%2Bfully%2Brotational%2Bservo%2Bmotors&qid=1688761387&s=electronics&sprefix=arduino%2Bfully%2Brotational%2Bservo%2Bmotors%2Celectronics%2C133&sr=1-17-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9idGY&th=1]"> Link </a> |
| Screws and Nuts| To assemble all the parts together and keep everything tightened | Only sold with Hexapod | <a href="[https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1]"> Link </a> |
| Crawling Robot Controller | Control the Hexapod | Only sold with Hexapod | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| WLAN Module | Allows the robot to have internet, letting phones with the app control it | $14 | <a href="[https://www.amazon.com/Hosyond-Wireless-Development-Compatible-Micropython/dp/B09SPWYS4B/ref=sr_1_3?crid=3DGQ3GPUNBPNB&dib=eyJ2IjoiMSJ9.b8AO89Yvq8W6pGbZ58J6QzCuZf_4u8y_M20-6EH1WU8NlNNSJXlEIiLRq6esXOdgtc5uDUq-8PkzPjAAyMt2cJ8P6L8UPBobph8v_f3RMKYyZy8Xh7SaXQdOphD9ht9vOxYikiCsGevgp8uGkKa9npIDzIU48EH3CJeFgo_OPw6-UkL1hfcAs-BropXCkmmNYk7r570legtSvJsqMI8Ti6td1X9_T8i5XPowV14zn94.Hbi46-SBmtQuriQ-1MS1He6aHxe5-BHO5Dy85lj-HmQ&dib_tag=se&keywords=esp8266%2Bwifi%2Bmodule&qid=1784650083&sprefix=ESP8266%2Caps%2C186&sr=8-3&th=1]"> Link </a> |
| Control Board | Remote's brain | $13 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Freenove-Compatible-Interface-Detailed-Instructions/dp/B0BVYCJY6D/ref=sr_1_4?crid=1UVDLLTYFICMY&dib=eyJ2IjoiMSJ9.Mocmx78_6P4MGpVvpSxchxc1qrjTnE3lGzm-g5WlcxsZUAjxwDOtMNoGaxxXHX5cPt4_yHPD0fbMnApY_tXQ6qFawMf9vJ5bRVTDMr3rIeUqlEfJTnoQJ2-TABgRtBqSvL_8niXEpdoB2WDhXCov4r6pfQbGvPtiLOCBZIAv8o1VQqTQwFbUE4H_0Q9vQVELZtiDDGEXA1YYWSf6URc2AOK6t7z8PwhBn06vn9VH05DQRBlDJmrbpcnqVsVNJFSyHaACi2sgG1sAFDU1hOoWKOaMOI9sw-TUmUU8WAZrMJ4.mg5ZEjsTF66HBzddiHNZkW_iAHzpRJoftDWRRR49qfQ&dib_tag=se&keywords=control+board+v4.0&qid=1784650265&sprefix=control+board+v4.0%2Caps%2C181&sr=8-4)"> Link </a> |
| Freenove Remote Shield | Keep the remote safe from damage | Only sold with Hexapod | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| 9V Battery Holder | Holder for the remote's battery | $7 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/DaierTek-Battery-Holder-Switch-Black/dp/B07YBZ18VS/ref=sr_1_6?crid=IXE4N7X9XMBF&dib=eyJ2IjoiMSJ9.XiI0ZK0KZHsTQAYYTJTZf6BxPuvPkl5Uw7fjyJfjMbluop1CzqTg-FXnjQJM7dxSmDRazPIbBPclmh98EBe7wNXqcF_6I3YXiawnXbJtT2ydOGFdjE38YrAe4uTJiadFY6d92WvWZxPz1rcVtvVcsni1UjHb_g_ZFj8BlqVJsakGWLuDKQZSexl96hLJxVLj6kZMPVcJduwPsGTi-dBDus0xdviXu6x9LAOqtKvpg9I.A7QF5_iTj8Upu76e0NmECPrcSrTa1lAqke9X5C6UfNo&dib_tag=se&keywords=9V+Battery+Holder&qid=1784650460&sprefix=9v+battery+hold%2Caps%2C175&sr=8-6)"> Link </a> |
| Wireless Module | Create bluetooth connection between controller and robot | $9 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/HiLetgo-Wireless-Transceiver-Development-Compatible/dp/B010N1ROQS/ref=sr_1_3?crid=VA6M1MWSN0RH&keywords=arduino%2Bwireless%2Bmodule&qid=1688761182&s=electronics&sprefix=arduino%2Bwireless%2Bmodule%2Celectronics%2C137&sr=1-3)&th=1)"> Link </a> |
| 7.2V Battery | Power the entire Hexapod | $25 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Tenergy-Capacity-Rechargeable-Replacement-Connectors/dp/B0037U35SO/ref=sr_1_7?crid=1TEPVKH32B1OM&dib=eyJ2IjoiMSJ9.gjLFk4KjNcKC78J407zTl62-V8vFaFMpA3LYQo8NHXr3dkpbE8nq0ry-ti2dRF2oNkfEAJ7a1CnsFN79A7LJ0BzZMp47pAB6MfZZcawDCfQPsbFX3SbZL_m3swMBWv-JRg4csJ2juCqYDEJmLFgXzmbr3lMzNxoTEeYL-R63Z9P6bSwPqwN2coEVgb3i0JrHQTfpB38tqy_W5beE5n0pP4Ogl9k-wSn_eIMEh_QysGpkUQboQszuta0LzADX39DLeWvUxi7qmKooj85gtuLNi0A4koSFs0urkJ12miKTlPA.iFErA26qn2-KrJ-RIOim3z7ydoorjBQ8_EgBXiHgUpY&dib_tag=se&keywords=7.2V%2BTenergy%2Bbattery&qid=1784650728&sprefix=7.2v%2Btenergy%2Bbatter%2Caps%2C207&sr=8-7&th=1)"> Link </a> |
| Cable Tidy | Keep the wires clean and out of the way | Only sold with Hexapod | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| 9V Battery Holder | Holder for the remote's battery | $7 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/DaierTek-Battery-Holder-Switch-Black/dp/B07YBZ18VS/ref=sr_1_6?crid=IXE4N7X9XMBF&dib=eyJ2IjoiMSJ9.XiI0ZK0KZHsTQAYYTJTZf6BxPuvPkl5Uw7fjyJfjMbluop1CzqTg-FXnjQJM7dxSmDRazPIbBPclmh98EBe7wNXqcF_6I3YXiawnXbJtT2ydOGFdjE38YrAe4uTJiadFY6d92WvWZxPz1rcVtvVcsni1UjHb_g_ZFj8BlqVJsakGWLuDKQZSexl96hLJxVLj6kZMPVcJduwPsGTi-dBDus0xdviXu6x9LAOqtKvpg9I.A7QF5_iTj8Upu76e0NmECPrcSrTa1lAqke9X5C6UfNo&dib_tag=se&keywords=9V+Battery+Holder&qid=1784650460&sprefix=9v+battery+hold%2Caps%2C175&sr=8-6)"> Link </a> |


# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
