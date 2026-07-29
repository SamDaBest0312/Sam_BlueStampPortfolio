# Hexapod
The Hexapod is a six-legged programmable robot inspired by insect movement. It has a durable acrylic body, with each leg powered by three servo motors for precise motion. Controlled by an Arduino board, it can be operated wirelessly using a smartphone, computer, or an Arduino-based controller. The Hexapod is designed for customization and provides a hands-on way to learn robotics and engineering.
q

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
Arduino UNO

  <img width="704" height="429" alt="image" src="https://github.com/user-attachments/assets/b30eb539-f655-4e15-a9f5-c931081caaf5" />
 

# Code

Hexapod Code

``` c++

#pragma once
#if defined(ARDUINO_AVR_MEGA2560)

#include <Arduino.h>
#include <Servo.h>
#include <EEPROM.h>
#include <FlexiTimer2.h>

class RobotShape
{
public:
  float a;
  float b;
  float g;
  float c;
  float d;
  float e;
  float f;
};

class EepromAddresses
{
public:
  static constexpr float dataFormatVersion = 0;
  static constexpr float productVersion = 3;

  static constexpr float servo22 = 100;
  static constexpr float servo23 = 102;
  static constexpr float servo24 = 104;
  static constexpr float servo25 = 106;
  static constexpr float servo26 = 108;
  static constexpr float servo27 = 110;
  static constexpr float servo28 = 112;
  static constexpr float servo29 = 114;
  static constexpr float servo30 = 116;
  static constexpr float servo39 = 118;
  static constexpr float servo38 = 120;
  static constexpr float servo37 = 122;
  static constexpr float servo36 = 124;
  static constexpr float servo35 = 126;
  static constexpr float servo34 = 128;
  static constexpr float servo33 = 130;
  static constexpr float servo32 = 132;
  static constexpr float servo31 = 134;

  static constexpr float robotState = 140;
};

class Power
{
public:
  Power();
  void Set(float adcReference, float samplingProportion, bool powerGroupAutoSwitch);

  bool powerGroupAutoSwitch;

  volatile float voltage;
  volatile bool powerGroupState;

  void Update();

private:
  const int samplingPin = A7;
  float adcReference;
  float samplingProportion;
  static const int samplingSize = 25;
  float samplingData[samplingSize];
  int samplingDataCounter = 0;
  static const int samplingPeakSize = 25;
  float samplingPeakData[samplingPeakSize];
  int samplingPeakDataCounter = 0;

  void Sampling();

  const int powerGroup1Pin = A15;
  const int powerGroup2Pin = A13;
  const int powerGroup3Pin = A14;
  const int powerGroupBootInterval = 5;
  const float powerGroupOnVoltage = 6.5;
  const float powerGroupOffVoltage = 5.5;
  bool powerGroup1State = false;
  bool powerGroup2State = false;
  bool powerGroup3State = false;

  void SetPowerGroupState(int group, bool state);

  int updateCounter = 0;
};

class Point
{
public:
  Point();
  Point(float x, float y, float z);

  static float GetDistance(Point point1, Point point2);

  volatile float x, y, z;
};

class RobotLegsPoints
{
public:
  RobotLegsPoints();
  RobotLegsPoints(Point leg1, Point leg2, Point leg3, Point leg4, Point leg5, Point leg6);

  Point leg1, leg2, leg3, leg4, leg5, leg6;
};

class RobotJoint
{
public:
  RobotJoint();
  void Set(int servoPin, float jointZero, bool jointDir, float jointMinAngle, float jointMaxAngle, int offsetAddress);

  void SetOffset(float offset);
  void SetOffsetEnableState(bool state);

  void RotateToDirectly(float jointAngle);

  float GetJointAngle(float servoAngle);

  bool CheckJointAngle(float jointAngle);

  volatile float jointAngleNow;
  volatile float servoAngleNow;

  static int firstRotateDelay;

private:
  Servo servo;
  int servoPin;
  float jointZero;
  bool jointDir;
  float jointMinAngle;
  float jointMaxAngle;
  int offsetAddress;
  volatile float offset = 0;
  volatile bool isOffsetEnable = true;
  volatile bool isFirstRotate = true;
};

class RobotLeg
{
public:
  RobotLeg();
  void Set(float xOrigin, float yOrigin, RobotShape robotShape);

  void SetOffsetEnableState(bool state);

  void CalculatePoint(float alpha, float beta, float gamma, volatile float &x, volatile float &y, volatile float &z);
  void CalculatePoint(float alpha, float beta, float gamma, Point &point);
  void CalculateAngle(float x, float y, float z, float &alpha, float &beta, float &gamma);
  void CalculateAngle(Point point, float &alpha, float &beta, float &gamma);

  bool CheckPoint(Point point);
  bool CheckAngle(float alpha, float beta, float gamma);

  void MoveTo(Point point);
  void MoveToRelatively(Point point);
  void WaitUntilFree();

  void ServosRotateTo(float angleA, float angleB, float angleC);

  void MoveToDirectly(Point point);
  void MoveToDirectlyRelatively(Point point);

  volatile bool isBusy = false;

  RobotJoint jointA, jointB, jointC;
  Point pointNow, pointGoal;

  static constexpr float negligibleDistance = 0.1;
  static constexpr float defaultStepDistance = 2;
  volatile float stepDistance = defaultStepDistance;

private:
  float xOrigin, yOrigin;
  RobotShape robotShape;
  volatile bool isFirstMove = true;

  void RotateToDirectly(float alpha, float beta, float gamma);
};

class Robot
{
public:
  Robot();
  void Start();

  enum State { Install, Calibrate, Boot, Action };
  State state = State::Boot;

  void InstallState();
  void CalibrateState();
  void CalibrateServos();
  void CalibrateVerify();
  void BootState();

  void MoveTo(RobotLegsPoints points);
  void MoveTo(RobotLegsPoints points, float speed);
  void MoveToRelatively(Point point);
  void MoveToRelatively(Point point, float speed);
  void WaitUntilFree();

  void SetSpeed(float speed);
  void SetSpeed(float speed1, float speed2, float speed3, float speed4, float speed5, float speed6);

  void SetSpeedMultiple(float multiple);

  bool CheckPoints(RobotLegsPoints points);

  void GetPointsNow(RobotLegsPoints &points);

  void Update();

  RobotLeg leg1, leg2, leg3, leg4, leg5, leg6;

  const RobotLegsPoints calibrateStatePoints = RobotLegsPoints(
    Point(-133, 100, 25),
    Point(-155, 0, 25),
    Point(-133, -100, 25),
    Point(133, 100, 25),
    Point(155, 0, 25),
    Point(133, -100, 25));
  const RobotLegsPoints calibratePoints = RobotLegsPoints(
    Point(-103, 85, 0),
    Point(-125, 0, 0),
    Point(-103, -85, 0),
    Point(103, 85, 0),
    Point(125, 0, 0),
    Point(103, -85, 0));
  const RobotLegsPoints bootPoints = RobotLegsPoints(
    Point(-81, 99, 0),
    Point(-115, 0, 0),
    Point(-81, -99, 0),
    Point(81, 99, 0),
    Point(115, 0, 0),
    Point(81, -99, 0));

  int dataFormatVersion;
  int productVersion;
  Power power;

private:
  volatile float speedMultiple = 1;

  void CalibrateLeg(RobotLeg &leg, Point calibratePoint);

  void UpdateAction();
  void UpdateLegAction(RobotLeg &leg);

  void MoveToDirectly(RobotLegsPoints points);

  void SetOffsetEnableState(bool state);

  RobotShape robotShape;
};

class RobotAction
{
public:
  RobotAction();
  void Start();

  void SetSpeedMultiple(float multiple);
  void SetActionGroup(int group);

  void ActiveMode();
  void SleepMode();
  void SwitchMode();

  void CrawlForward();
  void CrawlBackward();
  void CrawlLeft();
  void CrawlRight();
  void TurnLeft();
  void TurnRight();

  void Crawl(float x, float y, float angle);

  void ChangeBodyHeight(float height);

  void MoveBody(float x, float y, float z);
  void RotateBody(float x, float y, float z);

  void TwistBody(Point move, Point rotate);

  void InitialState();

  void LegMoveToRelatively(int leg, Point point);

  void LegMoveToRelativelyDirectly(int leg, Point point);

  Robot robot;

private:
  void ActionState();

  enum Mode { Active, Sleep };
  Mode mode = Mode::Sleep;

  enum LegsState { CrawlState, TwistBodyState, LegMoveState };
  LegsState legsState = LegsState::CrawlState;

  RobotLegsPoints initialPoints;
  RobotLegsPoints lastChangeLegsStatePoints;

  const float crawlLength = 42;
  const float turnAngle = 18;

  const float legLift = 20;
  const float legLiftSpeed = 7.5;
  const float defaultBodyLift = 15;
  float bodyLift = defaultBodyLift;
  const float bodyLiftSpeed = 1;

  const float minAlphaInterval = 0;

  int crawlSteps = 2;
  int legMoveIndex = 1;

  bool CheckCrawlPoints(RobotLegsPoints points);

  void GetCrawlPoints(RobotLegsPoints &points, Point point);
  void GetCrawlPoint(Point &point, Point direction);

  void GetTurnPoints(RobotLegsPoints &points, float angle);
  void GetTurnPoint(Point &point, float angle);

  const float speedTwistBody = 1.25;

  void TwistBody(Point move, Point rotateAxis, float rotateAngle);

  void GetMoveBodyPoints(RobotLegsPoints &points, Point point);
  void GetMoveBodyPoint(Point &point, Point direction);

  void GetRotateBodyPoints(RobotLegsPoints &points, Point rotateAxis, float rotateAngle);
  void GetRotateBodyPoint(Point &point, Point rotateAxis, float rotateAngle);

  void LegsMoveTo(RobotLegsPoints points);
  void LegsMoveTo(RobotLegsPoints points, float speed);
  void LegsMoveTo(RobotLegsPoints points, int leg, float legSpeed);
  void LegsMoveToRelatively(Point point, float speed);
};

#endif

```

0V7670 Camera Code

``` c
#include "setup.h"
#if EXAMPLE == 3
#include "Arduino.h"
#include "CameraOV7670.h"


// select resolution and communication speed:
//  1 - 115200bps 160x120 rgb
//  2 - 115200bps 160x120 grayscale
//  3 - 500000bps 160x120 rgb
//  4 - 500000bps 160x120 grayscale
//  5 - 500000bps 320x240 rgb
//  6 - 500000bps 320x240 grayscale
//  7 - 1Mbps 160x120 rgb
//  8 - 1Mbps 160x120 grayscale
//  9 - 1Mbps 320x240 rgb
// 10 - 1Mbps 320x240 grayscale
// 11 - 1Mbps 640x480 grayscale
// 12 - 2Mbps 160x120 rgb
// 13 - 2Mbps 160x120 grayscale
// 14 - 2Mbps 320x240 rgb
// 15 - 2Mbps 320x240 grayscale
// 16 - 2Mbps 640x480 rgb
// 17 - 2Mbps 640x480 grayscale
#define UART_MODE 10




const uint8_t VERSION = 0x10;
const uint8_t COMMAND_NEW_FRAME = 0x01 | VERSION;
const uint8_t COMMAND_DEBUG_DATA = 0x03 | VERSION;

const uint16_t UART_PIXEL_FORMAT_RGB565 = 0x01;
const uint16_t UART_PIXEL_FORMAT_GRAYSCALE = 0x02;

// Pixel byte parity check:
// Pixel Byte H: odd number of bits under H_BYTE_PARITY_CHECK and H_BYTE_PARITY_INVERT
// Pixel Byte L: even number of bits under L_BYTE_PARITY_CHECK and L_BYTE_PARITY_INVERT
//                                          H:RRRRRGGG
const uint8_t H_BYTE_PARITY_CHECK =  0b00100000;
const uint8_t H_BYTE_PARITY_INVERT = 0b00001000;
//                                          L:GGGBBBBB
const uint8_t L_BYTE_PARITY_CHECK =  0b00001000;
const uint8_t L_BYTE_PARITY_INVERT = 0b00100000;
// Since the parity for L byte can be zero we must ensure that the total byet value is above zero.
// Increasing the lowest bit of blue color is OK for that.
const uint8_t L_BYTE_PREVENT_ZERO  = 0b00000001;


const uint16_t COLOR_GREEN = 0x07E0;
const uint16_t COLOR_RED = 0xF800;



void processGrayscaleFrameBuffered();
void processGrayscaleFrameDirect();
void processRgbFrameBuffered();
void processRgbFrameDirect();
typedef void (*ProcessFrameData)(void) ;


#if UART_MODE==1
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 115200;
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_RGB565, 34);
#endif

#if UART_MODE==2
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 115200;
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_YUV422, 17);
#endif

#if UART_MODE==3
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 500000;
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_RGB565, 8);
#endif

#if UART_MODE==4
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 500000;
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_YUV422, 4);
#endif

#if UART_MODE==5
const uint16_t lineLength = 320;
const uint16_t lineCount = 240;
const uint32_t baud  = 500000;
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QVGA_320x240, CameraOV7670::PIXEL_RGB565, 32);
#endif

#if UART_MODE==6
const uint16_t lineLength = 320;
const uint16_t lineCount = 240;
const uint32_t baud  = 500000;
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QVGA_320x240, CameraOV7670::PIXEL_YUV422, 16);
#endif

#if UART_MODE==7
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 1000000;
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = false;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_RGB565, 5);
#endif

#if UART_MODE==8
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 1000000;
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = false;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_YUV422, 2);
#endif

#if UART_MODE==9
const uint16_t lineLength = 320;
const uint16_t lineCount = 240;
const uint32_t baud  = 1000000;
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QVGA_320x240, CameraOV7670::PIXEL_RGB565, 16);
#endif

#if UART_MODE==10
const uint16_t lineLength = 320;
const uint16_t lineCount = 240;
const uint32_t baud  = 1000000;
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QVGA_320x240, CameraOV7670::PIXEL_YUV422, 20);
#endif

#if UART_MODE==11
const uint16_t lineLength = 640;
const uint16_t lineCount = 480;
const uint32_t baud  = 1000000;
const ProcessFrameData processFrameData = processGrayscaleFrameDirect;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_VGA_640x480, CameraOV7670::PIXEL_RGB565, 16);
#endif

#if UART_MODE==12
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 2000000;
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = false;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_RGB565, 2);
#endif

#if UART_MODE==13
const uint16_t lineLength = 160;
const uint16_t lineCount = 120;
const uint32_t baud  = 2000000;
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = false;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QQVGA_160x120, CameraOV7670::PIXEL_YUV422, 2);
#endif

#if UART_MODE==14
const uint16_t lineLength = 320;
const uint16_t lineCount = 240;
const uint32_t baud  = 2000000; // may be unreliable
const ProcessFrameData processFrameData = processRgbFrameBuffered;
const uint16_t lineBufferLength = lineLength * 2;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QVGA_320x240, CameraOV7670::PIXEL_RGB565, 12);
#endif

#if UART_MODE==15
const uint16_t lineLength = 320;
const uint16_t lineCount = 240;
const uint32_t baud  = 2000000; // may be unreliable
const ProcessFrameData processFrameData = processGrayscaleFrameBuffered;
const uint16_t lineBufferLength = lineLength;
const bool isSendWhileBuffering = false;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_QVGA_320x240, CameraOV7670::PIXEL_YUV422, 6);
#endif

#if UART_MODE==16
const uint16_t lineLength = 640;
const uint16_t lineCount = 480;
const uint32_t baud  = 2000000;
const ProcessFrameData processFrameData = processRgbFrameDirect;
const uint16_t lineBufferLength = 1;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_RGB565;
CameraOV7670 camera(CameraOV7670::RESOLUTION_VGA_640x480, CameraOV7670::PIXEL_RGB565, 39);
#endif

#if UART_MODE==17
const uint16_t lineLength = 640;
const uint16_t lineCount = 480;
const uint32_t baud  = 2000000;
const ProcessFrameData processFrameData = processGrayscaleFrameDirect;
const uint16_t lineBufferLength = 1;
const bool isSendWhileBuffering = true;
const uint8_t uartPixelFormat = UART_PIXEL_FORMAT_GRAYSCALE;
CameraOV7670 camera(CameraOV7670::RESOLUTION_VGA_640x480, CameraOV7670::PIXEL_YUV422, 19);
#endif


uint8_t lineBuffer [lineBufferLength]; // Two bytes per pixel
uint8_t * lineBufferSendByte;
bool isLineBufferSendHighByte;
bool isLineBufferByteFormatted;

uint16_t frameCounter = 0;
uint16_t processedByteCountDuringCameraRead = 0;


void commandStartNewFrame(uint8_t pixelFormat);
void commandDebugPrint(const String debugText);
uint8_t sendNextCommandByte(uint8_t checksum, uint8_t commandByte);

void sendBlankFrame(uint16_t color);
inline void processNextGrayscalePixelByteInBuffer() __attribute__((always_inline));
inline void processNextRgbPixelByteInBuffer() __attribute__((always_inline));
inline void tryToSendNextRgbPixelByteInBuffer() __attribute__((always_inline));
inline void formatNextRgbPixelByteInBuffer() __attribute__((always_inline));
inline uint8_t formatRgbPixelByteH(uint8_t byte) __attribute__((always_inline));
inline uint8_t formatRgbPixelByteL(uint8_t byte) __attribute__((always_inline));
inline uint8_t formatPixelByteGrayscaleFirst(uint8_t byte) __attribute__((always_inline));
inline uint8_t formatPixelByteGrayscaleSecond(uint8_t byte) __attribute__((always_inline));
inline void waitForPreviousUartByteToBeSent() __attribute__((always_inline));
inline bool isUartReady() __attribute__((always_inline));



// this is called in Arduino setup() function
void initializeScreenAndCamera() {

  // Enable this for WAVGAT CPUs
  // For UART communiation we want to set WAVGAT Nano to 16Mhz to match Atmel based Arduino
  //CLKPR = 0x80; // enter clock rate change mode
  //CLKPR = 1; // set prescaler to 1. WAVGAT MCU has it 3 by default.

  Serial.begin(baud);
  if (camera.init()) {
    sendBlankFrame(COLOR_GREEN);
    delay(1000);
  } else {
    sendBlankFrame(COLOR_RED);
    delay(3000);
  }
}


void sendBlankFrame(uint16_t color) {
  uint8_t colorH = (color >> 8) & 0xFF;
  uint8_t colorL = color & 0xFF;

  commandStartNewFrame(UART_PIXEL_FORMAT_RGB565);
  for (uint16_t j=0; j<lineCount; j++) {
    for (uint16_t i=0; i<lineLength; i++) {
      waitForPreviousUartByteToBeSent();
      UDR0 = formatRgbPixelByteH(colorH);
      waitForPreviousUartByteToBeSent();
      UDR0 = formatRgbPixelByteL(colorL);
    }
  }
}




// this is called in Arduino loop() function
void processFrame() {
  processedByteCountDuringCameraRead = 0;
  commandStartNewFrame(uartPixelFormat);
  noInterrupts();
  processFrameData();
  interrupts();
  frameCounter++;
  commandDebugPrint("Frame " + String(frameCounter)/* + " " + String(processedByteCountDuringCameraRead)*/);
  //commandDebugPrint("Frame " + String(frameCounter, 16)); // send number in hexadecimal
}


void processGrayscaleFrameBuffered() {
  camera.waitForVsync();
  commandDebugPrint("Vsync");

  camera.ignoreVerticalPadding();

  for (uint16_t y = 0; y < lineCount; y++) {
    lineBufferSendByte = &lineBuffer[0];
    camera.ignoreHorizontalPaddingLeft();

    uint16_t x = 0;
    while ( x < lineBufferLength) {
      camera.waitForPixelClockRisingEdge(); // YUV422 grayscale byte
      camera.readPixelByte(lineBuffer[x]);
      lineBuffer[x] = formatPixelByteGrayscaleFirst(lineBuffer[x]);

      camera.waitForPixelClockRisingEdge(); // YUV422 color byte. Ignore.
      if (isSendWhileBuffering) {
        processNextGrayscalePixelByteInBuffer();
      }
      x++;

      camera.waitForPixelClockRisingEdge(); // YUV422 grayscale byte
      camera.readPixelByte(lineBuffer[x]);
      lineBuffer[x] = formatPixelByteGrayscaleSecond(lineBuffer[x]);

      camera.waitForPixelClockRisingEdge(); // YUV422 color byte. Ignore.
      if (isSendWhileBuffering) {
        processNextGrayscalePixelByteInBuffer();
      }
      x++;
    }
    camera.ignoreHorizontalPaddingRight();

    // Debug info to get some feedback how mutch data was processed during line read.
    processedByteCountDuringCameraRead = lineBufferSendByte - (&lineBuffer[0]);

    // Send rest of the line
    while (lineBufferSendByte < &lineBuffer[lineLength]) {
      processNextGrayscalePixelByteInBuffer();
    }
  };
}

void processNextGrayscalePixelByteInBuffer() {
  if (isUartReady()) {
    UDR0 = *lineBufferSendByte;
    lineBufferSendByte++;
  }
}


void processGrayscaleFrameDirect() {
  camera.waitForVsync();
  commandDebugPrint("Vsync");

  camera.ignoreVerticalPadding();

  for (uint16_t y = 0; y < lineCount; y++) {
    camera.ignoreHorizontalPaddingLeft();

    uint16_t x = 0;
    while ( x < lineLength) {
      camera.waitForPixelClockRisingEdge(); // YUV422 grayscale byte
      camera.readPixelByte(lineBuffer[0]);
      lineBuffer[0] = formatPixelByteGrayscaleFirst(lineBuffer[0]);

      camera.waitForPixelClockRisingEdge(); // YUV422 color byte. Ignore.
      waitForPreviousUartByteToBeSent();
      UDR0 = lineBuffer[0];
      x++;

      camera.waitForPixelClockRisingEdge(); // YUV422 grayscale byte
      camera.readPixelByte(lineBuffer[0]);
      lineBuffer[0] = formatPixelByteGrayscaleSecond(lineBuffer[0]);

      camera.waitForPixelClockRisingEdge(); // YUV422 color byte. Ignore.
      waitForPreviousUartByteToBeSent();
      UDR0 = lineBuffer[0];
      x++;
    }

    camera.ignoreHorizontalPaddingRight();
  }
}

uint8_t formatPixelByteGrayscaleFirst(uint8_t pixelByte) {
  // For the First byte in the parity chek byte pair the last bit is always 0.
  pixelByte &= 0b11111110;
  if (pixelByte == 0) {
    // Make pixel color always slightly above 0 since zero is a command marker.
    pixelByte |= 0b00000010;
  }
  return pixelByte;
}

uint8_t formatPixelByteGrayscaleSecond(uint8_t pixelByte) {
  // For the second byte in the parity chek byte pair the last bit is always 1.
  return pixelByte | 0b00000001;
}



void processRgbFrameBuffered() {
  camera.waitForVsync();
  commandDebugPrint("Vsync");

  camera.ignoreVerticalPadding();

  for (uint16_t y = 0; y < lineCount; y++) {
    lineBufferSendByte = &lineBuffer[0];
    isLineBufferSendHighByte = true; // Line starts with High byte
    isLineBufferByteFormatted = false;

    camera.ignoreHorizontalPaddingLeft();

    for (uint16_t x = 0; x < lineBufferLength;  x++) {
      camera.waitForPixelClockRisingEdge();
      camera.readPixelByte(lineBuffer[x]);
      if (isSendWhileBuffering) {
        processNextRgbPixelByteInBuffer();
      }
    };

    camera.ignoreHorizontalPaddingRight();

    // Debug info to get some feedback how mutch data was processed during line read.
    processedByteCountDuringCameraRead = lineBufferSendByte - (&lineBuffer[0]);

    // send rest of the line
    while (lineBufferSendByte < &lineBuffer[lineLength * 2]) {
      processNextRgbPixelByteInBuffer();
    }
  }
}

void processNextRgbPixelByteInBuffer() {
  // Format pixel bytes and send out in different cycles.
  // There is not enough time to do both on faster frame rates.
  if (isLineBufferByteFormatted) {
    tryToSendNextRgbPixelByteInBuffer();
  } else {
    formatNextRgbPixelByteInBuffer();
  }
}

void tryToSendNextRgbPixelByteInBuffer() {
  if (isUartReady()) {
    UDR0 = *lineBufferSendByte;
    lineBufferSendByte++;
    isLineBufferByteFormatted = false;
  }
}

void formatNextRgbPixelByteInBuffer() {
  if (isLineBufferSendHighByte) {
    *lineBufferSendByte = formatRgbPixelByteH(*lineBufferSendByte);
  } else {
    *lineBufferSendByte = formatRgbPixelByteL(*lineBufferSendByte);
  }
  isLineBufferByteFormatted = true;
  isLineBufferSendHighByte = !isLineBufferSendHighByte;
}




void processRgbFrameDirect() {
  camera.waitForVsync();
  commandDebugPrint("Vsync");

  camera.ignoreVerticalPadding();

  for (uint16_t y = 0; y < lineCount; y++) {
    camera.ignoreHorizontalPaddingLeft();
    
    for (uint16_t x = 0; x < lineLength; x++) {
      
      camera.waitForPixelClockRisingEdge();
      camera.readPixelByte(lineBuffer[0]);
      lineBuffer[0] = formatRgbPixelByteH(lineBuffer[0]);
      waitForPreviousUartByteToBeSent();
      UDR0 = lineBuffer[0];
      
      camera.waitForPixelClockRisingEdge();
      camera.readPixelByte(lineBuffer[0]);
      lineBuffer[0] = formatRgbPixelByteL(lineBuffer[0]);
      waitForPreviousUartByteToBeSent();
      UDR0 = lineBuffer[0];
    }
    
    camera.ignoreHorizontalPaddingRight();
  };
}


// RRRRRGGG
uint8_t formatRgbPixelByteH(uint8_t pixelByteH) {
  // Make sure that
  // A: pixel color always slightly above 0 since zero is end of line marker
  // B: odd number of bits for H byte under H_BYTE_PARITY_CHECK and H_BYTE_PARITY_INVERT to enable error correction
  if (pixelByteH & H_BYTE_PARITY_CHECK) {
    return pixelByteH & (~H_BYTE_PARITY_INVERT);
  } else {
    return pixelByteH | H_BYTE_PARITY_INVERT;
  }
}


// GGGBBBBB
uint8_t formatRgbPixelByteL(uint8_t pixelByteL) {
  // Make sure that
  // A: pixel color always slightly above 0 since zero is end of line marker
  // B: even number of bits for L byte under L_BYTE_PARITY_CHECK and L_BYTE_PARITY_INVERT to enable error correction
  if (pixelByteL & L_BYTE_PARITY_CHECK) {
    return pixelByteL | L_BYTE_PARITY_INVERT | L_BYTE_PREVENT_ZERO;
  } else {
    return (pixelByteL & (~L_BYTE_PARITY_INVERT)) | L_BYTE_PREVENT_ZERO;
  }
}









void commandStartNewFrame(uint8_t pixelFormat) {
  waitForPreviousUartByteToBeSent();
  UDR0 = 0x00; // New command

  waitForPreviousUartByteToBeSent();
  UDR0 = 4; // Command length

  uint8_t checksum = 0;
  checksum = sendNextCommandByte(checksum, COMMAND_NEW_FRAME);
  checksum = sendNextCommandByte(checksum, lineLength & 0xFF); // lower 8 bits of image width
  checksum = sendNextCommandByte(checksum, lineCount & 0xFF); // lower 8 bits of image height
  checksum = sendNextCommandByte(checksum, 
      ((lineLength >> 8) & 0x03) // higher 2 bits of image width
      | ((lineCount >> 6) & 0x0C) // higher 2 bits of image height
      | ((pixelFormat << 4) & 0xF0));

  waitForPreviousUartByteToBeSent();
  UDR0 = checksum;
}


void commandDebugPrint(const String debugText) {
  if (debugText.length() > 0) {
    
    waitForPreviousUartByteToBeSent();
    UDR0 = 0x00; // New commnad

    waitForPreviousUartByteToBeSent();
    UDR0 = debugText.length() + 1; // Command length. +1 for command code.
    
    uint8_t checksum = 0;
    checksum = sendNextCommandByte(checksum, COMMAND_DEBUG_DATA);
    for (uint16_t i=0; i<debugText.length(); i++) {
      checksum = sendNextCommandByte(checksum, debugText[i]);
    }

    waitForPreviousUartByteToBeSent();
    UDR0 = checksum;
  }
}


uint8_t sendNextCommandByte(uint8_t checksum, uint8_t commandByte) {
  waitForPreviousUartByteToBeSent();
  UDR0 = commandByte;
  return checksum ^ commandByte;
}




void waitForPreviousUartByteToBeSent() {
  while(!isUartReady()); //wait for byte to transmit
}


bool isUartReady() {
  return UCSR0A & (1<<UDRE0);
}


#endif

```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Calibration Graph | Brain of the Hexapod | Only sold with Hexapod | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1"> Link </a> |
| Acrylic Parts (Robot and Remote set) | Structure and main parts of the Hexapod | Only sold with Hexapod | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1"> Link </a> |
| Servos (18) | Rotation and movement of the Hexapod limbs | $17 | <a href="https://www.amazon.com/Hosyond-MG996R-Digital-Motors-Helicopter/dp/B0BYD9M1P3/ref=sr_1_17_sspa?crid=3TW5W06Y90D49&keywords=arduino%2Bfully%2Brotational%2Bservo%2Bmotors&qid=1688761387&s=electronics&sprefix=arduino%2Bfully%2Brotational%2Bservo%2Bmotors%2Celectronics%2C133&sr=1-17-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9idGY&th=1"> Link </a> |
| Screws and Nuts| To assemble all the parts together and keep everything tightened | Only sold with Hexapod | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1"> Link </a> |
| Crawling Robot Controller | Control the Hexapod | Only sold with Hexapod | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1"> Link </a> |
| WLAN Module | Allows the robot to have internet, letting phones with the app control it | $14 | <a href="https://www.amazon.com/Hosyond-Wireless-Development-Compatible-Micropython/dp/B09SPWYS4B/ref=sr_1_3?crid=3DGQ3GPUNBPNB&dib=eyJ2IjoiMSJ9.b8AO89Yvq8W6pGbZ58J6QzCuZf_4u8y_M20-6EH1WU8NlNNSJXlEIiLRq6esXOdgtc5uDUq-8PkzPjAAyMt2cJ8P6L8UPBobph8v_f3RMKYyZy8Xh7SaXQdOphD9ht9vOxYikiCsGevgp8uGkKa9npIDzIU48EH3CJeFgo_OPw6-UkL1hfcAs-BropXCkmmNYk7r570legtSvJsqMI8Ti6td1X9_T8i5XPowV14zn94.Hbi46-SBmtQuriQ-1MS1He6aHxe5-BHO5Dy85lj-HmQ&dib_tag=se&keywords=esp8266%2Bwifi%2Bmodule&qid=1784650083&sprefix=ESP8266%2Caps%2C186&sr=8-3&th=1"> Link </a> |
| Control Board | Remote's brain | $13 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Freenove-Compatible-Interface-Detailed-Instructions/dp/B0BVYCJY6D/ref=sr_1_4?crid=1UVDLLTYFICMY&dib=eyJ2IjoiMSJ9.Mocmx78_6P4MGpVvpSxchxc1qrjTnE3lGzm-g5WlcxsZUAjxwDOtMNoGaxxXHX5cPt4_yHPD0fbMnApY_tXQ6qFawMf9vJ5bRVTDMr3rIeUqlEfJTnoQJ2-TABgRtBqSvL_8niXEpdoB2WDhXCov4r6pfQbGvPtiLOCBZIAv8o1VQqTQwFbUE4H_0Q9vQVELZtiDDGEXA1YYWSf6URc2AOK6t7z8PwhBn06vn9VH05DQRBlDJmrbpcnqVsVNJFSyHaACi2sgG1sAFDU1hOoWKOaMOI9sw-TUmUU8WAZrMJ4.mg5ZEjsTF66HBzddiHNZkW_iAHzpRJoftDWRRR49qfQ&dib_tag=se&keywords=control+board+v4.0&qid=1784650265&sprefix=control+board+v4.0%2Caps%2C181&sr=8-4)"> Link </a> |
| Freenove Remote Shield | Keep the remote safe from damage | Only sold with Hexapod | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1"> Link </a> |
| 9V Battery Holder | Holder for the remote's battery | $7 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/DaierTek-Battery-Holder-Switch-Black/dp/B07YBZ18VS/ref=sr_1_6?crid=IXE4N7X9XMBF&dib=eyJ2IjoiMSJ9.XiI0ZK0KZHsTQAYYTJTZf6BxPuvPkl5Uw7fjyJfjMbluop1CzqTg-FXnjQJM7dxSmDRazPIbBPclmh98EBe7wNXqcF_6I3YXiawnXbJtT2ydOGFdjE38YrAe4uTJiadFY6d92WvWZxPz1rcVtvVcsni1UjHb_g_ZFj8BlqVJsakGWLuDKQZSexl96hLJxVLj6kZMPVcJduwPsGTi-dBDus0xdviXu6x9LAOqtKvpg9I.A7QF5_iTj8Upu76e0NmECPrcSrTa1lAqke9X5C6UfNo&dib_tag=se&keywords=9V+Battery+Holder&qid=1784650460&sprefix=9v+battery+hold%2Caps%2C175&sr=8-6)"> Link </a> |
| Wireless Module | Create bluetooth connection between controller and robot | $9 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/HiLetgo-Wireless-Transceiver-Development-Compatible/dp/B010N1ROQS/ref=sr_1_3?crid=VA6M1MWSN0RH&keywords=arduino%2Bwireless%2Bmodule&qid=1688761182&s=electronics&sprefix=arduino%2Bwireless%2Bmodule%2Celectronics%2C137&sr=1-3)&th=1)"> Link </a> |
| 7.2V Battery | Power the entire Hexapod | $25 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Tenergy-Capacity-Rechargeable-Replacement-Connectors/dp/B0037U35SO/ref=sr_1_7?crid=1TEPVKH32B1OM&dib=eyJ2IjoiMSJ9.gjLFk4KjNcKC78J407zTl62-V8vFaFMpA3LYQo8NHXr3dkpbE8nq0ry-ti2dRF2oNkfEAJ7a1CnsFN79A7LJ0BzZMp47pAB6MfZZcawDCfQPsbFX3SbZL_m3swMBWv-JRg4csJ2juCqYDEJmLFgXzmbr3lMzNxoTEeYL-R63Z9P6bSwPqwN2coEVgb3i0JrHQTfpB38tqy_W5beE5n0pP4Ogl9k-wSn_eIMEh_QysGpkUQboQszuta0LzADX39DLeWvUxi7qmKooj85gtuLNi0A4koSFs0urkJ12miKTlPA.iFErA26qn2-KrJ-RIOim3z7ydoorjBQ8_EgBXiHgUpY&dib_tag=se&keywords=7.2V%2BTenergy%2Bbattery&qid=1784650728&sprefix=7.2v%2Btenergy%2Bbatter%2Caps%2C207&sr=8-7&th=1)"> Link </a> |
| Cable Tidy | Keep the wires clean and out of the way | Only sold with Hexapod | <a href="https://www.amazon.com/Freenove-Raspberry-Crawling-Detailed-Tutorial/dp/B07FLVZ2DN/ref=sr_1_3?crid=10MZ420A7CL5A&dib=eyJ2IjoiMSJ9.hyUjFCpcxtDvB6cSLdESXTY436oZlRkuTYKG0JfizYCq1_ZZVTbLEFVYsDM-pPWfCwsOMlmmURsyZ9cW_iF9gRrVmt-RQ8hrsqenyVERBkgqfayOo44lk2hZfnMgnVNDzxXd2wAWehYwfQm6fBlTIKKaxLxqO5kwVtiKRMQ3rq6CYH19LIrI-_ixDnrj06vpgbbRiD-N5DpfgLeV_XEGliCUxgWuxIADoykxqSvgkAeuXzpQipb53Y0uHU46Xp2t2t8GW3RstrmZ9rGIRucnRD-uA6HZG5CFdFCONfQiaSc.KV67qdpoGLse8jsJYbLY7pkWrU714tQJTBjr8bBxp_o&dib_tag=se&keywords=Freenove%2BHexapod%2BRobot%2BKit&qid=1784649369&sprefix=freenove%2Bhexapod%2Brobot%2Bki%2Caps%2C169&sr=8-3&th=1"> Link </a> |
| 9V Battery Holder | Holder for the remote's battery | $7 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/DaierTek-Battery-Holder-Switch-Black/dp/B07YBZ18VS/ref=sr_1_6?crid=IXE4N7X9XMBF&dib=eyJ2IjoiMSJ9.XiI0ZK0KZHsTQAYYTJTZf6BxPuvPkl5Uw7fjyJfjMbluop1CzqTg-FXnjQJM7dxSmDRazPIbBPclmh98EBe7wNXqcF_6I3YXiawnXbJtT2ydOGFdjE38YrAe4uTJiadFY6d92WvWZxPz1rcVtvVcsni1UjHb_g_ZFj8BlqVJsakGWLuDKQZSexl96hLJxVLj6kZMPVcJduwPsGTi-dBDus0xdviXu6x9LAOqtKvpg9I.A7QF5_iTj8Upu76e0NmECPrcSrTa1lAqke9X5C6UfNo&dib_tag=se&keywords=9V+Battery+Holder&qid=1784650460&sprefix=9v+battery+hold%2Caps%2C175&sr=8-6)"> Link </a> |


# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
