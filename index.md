# Mecanum/Omniwheel Delivery Robot

Are interested to see the mind of an engineer by how they think, build, and 

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Alex P | Kehilah Jewish High School | Computer Science and Engineering | Incoming Freshman

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](IMG_047.png)
  
# Final Milestone

During my time at BlueStamp, I embarked on a remarkable journey of transforming from a person who barely knew how to follow a manual to create a robot to a someone who to make a futuristic-like robot with a cool trailer capable of delivering items to my brother's room. It was not an easy task, as I encountered numerous technical challenges along the way. From learning the intricacies of wiring to ensuring that all the components were assembled correctly, I had to rely on my problem-solving skills and a thirst for knowledge to overcome these obstacles. Each step of the process was a learning experience. I delved into the world of robotics, absorbing information about circuitry, motors, and sensors. I studied the inner workings of my robot, experimenting and fine-tuning to optimize its performance. It was a journey that demanded patience, attention to detail, and a willingness to persevere when faced with setbacks. But it was all worth it. The moment my robot successfully maneuvered its way through the room, delivering items to my brother's delight, I experienced an overwhelming sense of accomplishment and joy. The satisfaction derived from solving complex technical issues and witnessing the tangible results of my efforts was unparalleled. Throughout this transformative experience, I learned valuable lessons that extend beyond the realm of robotics. I discovered the importance of embracing challenges and taking risks. By pushing myself out of my comfort zone, I not only enhanced my technical skills but also developed a mindset of resilience and adaptability. The fusion of coding and hardware opened up new possibilities, expanding my horizons and revealing the boundless potential that lies at the intersection of different disciplines. As I reflect on my journey, I realize that this camp has ignited a passion within me. I aspire to pursue a career as a mechanical and software engineer, where I can channel my enthusiasm for robotics into creating innovative rovers and probes for space exploration. The idea of contributing to the advancement of scientific knowledge and exploring the mysteries of the universe fills me with excitement and a sense of purpose. In the future, I envision myself working alongside brilliant minds, collaborating on groundbreaking projects that push the boundaries of what is possible. I am determined to continue learning, growing, and embracing new challenges as I strive to make a meaningful impact in the field of robotics and beyond.

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# First Milestone

My project is a Omniwheel/Mecanum wheel robot. The robot came as a kit with a manual. I basically followed the manual to build the robot. Keep in my mind, it wasn't that simple. It wasn't like "follow the manual and you will have a fully functioning robot in no time!" Not at all. While following the manual, it was at time very frustrating. Sometimes I would put a motor backwards, put the screws the opposite way, or at times have everything literally swapped the opposite way. This is when I had to troubel shoot. My instructor would tell me to list out every possible problem that there could be in my code, wiring, and robot structure. I would then work through everything in that list hoping to fix the issue. Once I was done with completing the manual and I had a bare bone-fuunctioning robot. I thought about modifications. I asked myself: "How cool would it be if I could make my robot use navigation plans to deliver items to people's door?" When I proposed that idea, my instructor said to think even bigger. So then I said "How cool would it be to have a robot that delivers packages and has a system that allows a drone to land on it?" That is when my instructor said "interesting." So my plan now is to attach a trailer to my robot and later on think about adding a carrier system. I may face challenges like crashing my robot or not knowing why my robot is driving into a wall, but I'm ready to face them!

<iframe width="560" height="315" src="https://www.youtube.com/embed/6ndPc5qHybc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Schematics 

Here are images and diagrams of my wiring and motor placement.

![Headstone Image](Screen Shot 2023-06-21 at 1.43.33 PM.png)
![Headstone Image](Screen Shot 2023-06-21 at 1.44.28 PM.png)
![Headstone Image](Screen Shot 2023-06-21 at 1.44.59 PM.png)

# Code

Feel free to take a good look at my code. Keep in mind this the first version of code I wrote for my robot due to this only being Milestone One.

```c++
#define SPEED 200    
#define TURN_SPEED 200    
#define speedPinR 9   //  Front Wheel PWM pin connect Model-Y M_B ENA 
#define RightMotorDirPin1  22    //Front Right Motor direction pin 1 to Model-Y M_B IN1  (K1)
#define RightMotorDirPin2  24   //Front Right Motor direction pin 2 to Model-Y M_B IN2   (K1)                                 
#define LeftMotorDirPin1  26    //Front Left Motor direction pin 1 to Model-Y M_B IN3 (K3)
#define LeftMotorDirPin2  28   //Front Left Motor direction pin 2 to Model-Y M_B IN4 (K3)
#define speedPinL 10   //  Front Wheel PWM pin connect Model-Y M_B ENB

#define speedPinRB 11   //  Rear Wheel PWM pin connect Left Model-Y M_A ENA 
#define RightMotorDirPin1B  5    //Rear Right Motor direction pin 1 to Model-Y M_A IN1 ( K1)
#define RightMotorDirPin2B 6    //Rear Right Motor direction pin 2 to Model-Y M_A IN2 ( K1) 
#define LeftMotorDirPin1B 7    //Rear Left Motor direction pin 1 to Model-Y M_A IN3  (K3)
#define LeftMotorDirPin2B 8  //Rear Left Motor direction pin 2 to Model-Y M_A IN4 (K3)
#define speedPinLB 12    //  Rear Wheel PWM pin connect Model-Y M_A ENB

/*motor control*/
void go_advance(int speed){
   RL_fwd(speed);
   RR_fwd(speed);
   FR_fwd(speed);
   FL_fwd(speed); 
}
void go_back(int speed){
   RL_bck(speed);
   RR_bck(speed);
   FR_bck(speed);
   FL_bck(speed); 
}
void right_shift(int speed_fl_fwd,int speed_rl_bck ,int speed_rr_fwd,int speed_fr_bck) {
  FL_fwd(speed_fl_fwd); 
  RL_bck(speed_rl_bck); 
  RR_fwd(speed_rr_fwd);
  FR_bck(speed_fr_bck);
}
void left_shift(int speed_fl_bck,int speed_rl_fwd ,int speed_rr_bck,int speed_fr_fwd){
   FL_bck(speed_fl_bck);
   RL_fwd(speed_rl_fwd);
   RR_bck(speed_rr_bck);
   FR_fwd(speed_fr_fwd);
}

void left_turn(int speed){
   RL_bck(0);
   RR_fwd(speed);
   FR_fwd(speed);
   FL_bck(0); 
}
void right_turn(int speed){
 //  RL_fwd(speed);
//   RR_bck(0);
 //  FR_bck(0);
 //  FL_fwd(speed); 

   RL_fwd(speed);
   RR_fwd(0);
   FR_fwd(0);
   FL_fwd(speed); 
}
void left_back(int speed){
   RL_fwd(0);
   RR_bck(speed);
   FR_bck(speed);
   FL_fwd(0); 
}
void right_back(int speed){
   RL_bck(speed);
   RR_fwd(0);
   FR_fwd(0);
   FL_bck(speed); 
}
void clockwise(int speed){
   RL_fwd(speed);
   RR_bck(speed);
   FR_bck(speed);
   FL_fwd(speed); 
}
void countclockwise(int speed){
   RL_bck(speed);
   RR_fwd(speed);
   FR_fwd(speed);
   FL_bck(speed); 
}


void FR_fwd(int speed)  //front-right wheel forward turn
{
  digitalWrite(RightMotorDirPin1,HIGH);
  digitalWrite(RightMotorDirPin2,LOW); 
  analogWrite(speedPinR,speed);
}
void FR_bck(int speed) // front-right wheel backward turn
{
  digitalWrite(RightMotorDirPin1,LOW);
  digitalWrite(RightMotorDirPin2,HIGH); 
  analogWrite(speedPinR,speed);
}
void FL_fwd(int speed) // front-left wheel forward turn
{
  digitalWrite(LeftMotorDirPin1,HIGH);
  digitalWrite(LeftMotorDirPin2,LOW);
  analogWrite(speedPinL,speed);
}
void FL_bck(int speed) // front-left wheel backward turn
{
  digitalWrite(LeftMotorDirPin1,LOW);
  digitalWrite(LeftMotorDirPin2,HIGH);
  analogWrite(speedPinL,speed);
}

void RR_fwd(int speed)  //rear-right wheel forward turn
{
  digitalWrite(RightMotorDirPin1B, HIGH);
  digitalWrite(RightMotorDirPin2B,LOW); 
  analogWrite(speedPinRB,speed);
}
void RR_bck(int speed)  //rear-right wheel backward turn
{
  digitalWrite(RightMotorDirPin1B, LOW);
  digitalWrite(RightMotorDirPin2B,HIGH); 
  analogWrite(speedPinRB,speed);
}
void RL_fwd(int speed)  //rear-left wheel forward turn
{
  digitalWrite(LeftMotorDirPin1B,HIGH);
  digitalWrite(LeftMotorDirPin2B,LOW);
  analogWrite(speedPinLB,speed);
}
void RL_bck(int speed)    //rear-left wheel backward turn
{
  digitalWrite(LeftMotorDirPin1B,LOW);
  digitalWrite(LeftMotorDirPin2B,HIGH);
  analogWrite(speedPinLB,speed);
}
 
void stop_Stop()    //Stop
{
  analogWrite(speedPinLB,0);
  analogWrite(speedPinRB,0);
  analogWrite(speedPinL,0);
  analogWrite(speedPinR,0);
}


//Pins initialize
void init_GPIO()
{
  pinMode(RightMotorDirPin1, OUTPUT); 
  pinMode(RightMotorDirPin2, OUTPUT); 
  pinMode(speedPinL, OUTPUT);  
 
  pinMode(LeftMotorDirPin1, OUTPUT);
  pinMode(LeftMotorDirPin2, OUTPUT); 
  pinMode(speedPinR, OUTPUT);
  pinMode(RightMotorDirPin1B, OUTPUT); 
  pinMode(RightMotorDirPin2B, OUTPUT); 
  pinMode(speedPinLB, OUTPUT);  
 
  pinMode(LeftMotorDirPin1B, OUTPUT);
  pinMode(LeftMotorDirPin2B, OUTPUT); 
  pinMode(speedPinRB, OUTPUT);
   
  stop_Stop();
}

void setup()
{
  init_GPIO();


go_advance(SPEED);
     delay(3000);
     stop_Stop();
     delay(1000);
  
go_back(SPEED);
      delay(3000);
      stop_Stop();
      delay(1000);

/*	  
left_turn(TURN_SPEED);
      delay(1000);
      stop_Stop();
      delay(1000);
	  
right_turn(TURN_SPEED);
     delay(1000);
     stop_Stop();
     delay(1000);
  
right_shift(200,200,200,200); //right shift
     delay(1000);
     stop_Stop();
     delay(1000);

left_shift(200,200,200,200); //left shift
     delay(1000);
     stop_Stop();
     delay(1000);
	 
left_shift(200,0,200,0); //left diagonal back
     delay(1000);
     stop_Stop();
	 delay(1000);
 
right_shift(200,0,200,0); //right diagonal ahead
     delay(1000);
     stop_Stop();
	 delay(1000);

left_shift(0,200,0,200); //left diagonal ahead
     delay(1000);
     stop_Stop();
     delay(1000);

right_shift(0,200,0,200); //right diagonal back
     delay(1000);
     stop_Stop();
	 delay(1000);

*/

}

void loop(){
}

```

# Bill of Materials

If you are wondering where I got my materials, here they are. Because my robot came in a kit some of the parts aren't for individual sail. So I found similair items that are approximately the same price.








| Part  | Description | Price | Link | 
| :-: | :-: | :-: | :-: | 
| Arduino Mega and USB Cord  | Used to interact with energy by using code  | $20.99  | <a href="https://www.amazon.com/ELEGOO-ATmega2560-ATMEGA16U2-Projects-Compliant/dp/B01H4ZLZLQ/ref=asc_df_B01H4ZLZLQ/?tag=hyprod-20&linkCode=df0&hvadid=309743296044&hvpos=&hvnetw=g&hvrand=12310535526926751668&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9031968&hvtargid=pla-490931309987&th=1"> Link </a> | 
| Mecanum Wheels  | The wheels of the robot  | $29.99 | <a href="https://www.amazon.com/Omni-Directional-Hardness-Intelligent-Components-Accessories/dp/B096HWF3S9"> Link </a> |
| Amazon AA Batteries  | powers the circuit  | $9.29 | <a href="https://www.amazon.com/AmazonBasics-Performance-Alkaline-Batteries-12-Pack/dp/B07KWYGTC6"> Link </a> |
| Osoyoo IR Transmitters  | IR Transmission  | $9.96 | <a href="https://www.amazon.com/OSOYOO-Infrared-Obstacle-Avoidance-Arduino/dp/B01I57HIJ0?ref_=ast_sto_dp"> Link </a> |
| OSOYOO Infrared Line Tracking Sensor Module  | Reflection Tracking  | $9.99 | <a href="https://www.amazon.com/OSOYOO-5-Line-Tracking-Sensor-Female/dp/B091BRVBXD?ref_=ast_sto_dp"> Link </a> |
| Wires  | These aren't the exact wires I used but they are the closest ones I can find.  | $9.99 | <a href="https://www.amazon.com/Elegoo-EL-CP-004-Multicolored-Breadboard-arduino/dp/B01EV70C78/ref=sr_1_1_sspa?crid=3RA9E5VC4FLUM&keywords=female%2Bwires&qid=1687376818&sprefix=female%2Bwire%2Caps%2C196&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1"> Link </a> |
| Battery Pack  | Holds the AA batteries  | $6.48 | <a href="https://www.amazon.com/LAMPVPATH-Battery-Holder-Leads-Wires/dp/B07T7MTRZX/ref=sr_1_3?crid=IVV96333EFPX&keywords=4+AA+Battery+Holder&qid=1687377014&s=electronics&sprefix=%2Celectronics%2C144&sr=1-3"> Link </a> |
| Gear Motor Dual Shaft 3-6V L Shape TT Motor  | Turns the wheels  | $8.99 | <a href="https://www.amazon.com/Antrader-Motor-Shaft-Arduino-Smart/dp/B07S6NFNWZ/ref=sr_1_36?keywords=motors&qid=1687377100&sr=8-36&th=1"> Link </a> | 
| Voltage Meter  | Displays the voltage  | $9.99 | <a href="https://www.amazon.com/RuiLing-Digital-Voltmeter-Electromobile-Motorcycle/dp/B07THN5TRS/ref=sr_1_3_sspa?crid=Q2WW1B12PKDH&keywords=1+voltage+meter&qid=1687377330&sprefix=1+voltage+meter%2Caps%2C145&sr=8-3-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1"> Link </a> |
| Servo Motor  | rotate and push parts with precision  | $10.16 | <a href="https://www.amazon.com/Servo-Motors-Sub-Micro-SG51R-piece/dp/B0137LG0KW/ref=sr_1_1_sspa?crid=32UA5D9177IHH&keywords=servo+motor&qid=1687377605&sprefix=servo+moto%2Caps%2C160&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1&smid=AM0JQO74J587C"> Link </a> |
| OSOYOO ESP8266 WiFi shield  | Allows an Arduino board to connect to the internet using the WiFi library and to read and write an SD card using the SD library  | N/A | <a href="www.something.com"> N/A </a> |
