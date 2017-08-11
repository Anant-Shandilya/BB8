# BB8
Applications
Starwars BB8 model has varied applications, it’s implementation scale can be pitched from a all terrain vehicle to a space rover. The robot can be used for navigation, patrolling, communication and other purposes. The best part of our robot is that it will never topple, this tragedy occurred with Mars rover “Discovery” which toppled and suffered serious complications. Coming on navigation part , since the robot’s movement mechanism is based on shifting of COG of the body inside the outer sphere and the contact area is almost equivalent in all surfaces hence the robot can easily navigate maneuvering different kinds of surfaces.

The head of the BB8 model is detachable , hence it can be used to install various kinds of plug-ins like a communication enhancing network creation antennae can be installed in the head , a camera assemble can be embedded in the head which can help in patrolling  remote areas and also for spying purposes since the size of the robot can be varied according to the need. 


WORKING

The robot comprises of 3 parts:- 
1- Head Assembly
2- Outer Sphere
3- Internal Mechanism

HEAD ASSEMBLY
Head assembly comprises of a semi spherical thermocol shell. Inside the shell was installed an assembly of magnets and castor wheels. These magnets were paired with the  magnets placed on the top of the internal mechnism. When the internal body rotates it’s top using a DC motor,the paired magnets make  the top move accordingly.

OUTER SPHERE
Outer Sphere is the surface contact part of the bot . It contains the internal mechanism which moves inside it to shift centre of gravity of the bot and once the COG shifts from the base , the system becomes unbalanced and the Outer sphere moves in the same direction to normalize this change and reduce system’s potential energy.

INTERNAL MECHANISM
The internal mechanism comprises of a circular base and differential drive. The internal mechanism has low center of gravity (added weight) .The drive consists of two traction wheels paired on two DC motors . The mechanism moves inside the outer sphere and climbs the wall of the sphere. A net torque is applied on the center of mass of the system and the outer sphere rolls in the same direction to lower the internal mechanism. To change the direction of motion, the wheels are rotated in opposite direction while the bot remains stationary , the internal mechanism aligns itself into different direction.

CODE
//ArduinoUNO
//BB8
 // according to our mobile app input to HC05 : Forward 70 backward : 66 right : 82 left : 76 and no input : 83
int pwm_2=3;
int pwm_1=5;
int dir_2=10;
int dir_1=11;
int state;
void setup() {
   
    pinMode(pwm_2, OUTPUT);
    pinMode(pwm_1, OUTPUT);
    pinMode(dir_1, OUTPUT);
    pinMode(dir_2, OUTPUT);
 
    Serial.begin(9600);


}
void loop() {

   if(Serial.available() > 0){     
      state = Serial.read(); 
      Serial.println(state);  
      
    }
    
    //forward
    if (state == 70) {
        digitalWrite(pwm_1, HIGH);
        digitalWrite(pwm_2, HIGH); 
        digitalWrite(dir_1, HIGH);
        digitalWrite(dir_2, HIGH);
        
          Serial.println("Go Forward!");
          delay(5);
          
        }
    
    
    // turn left
    else if (state == 76) {
        analogWrite(pwm_1, 80); 
        digitalWrite(dir_1, HIGH); 
        analogWrite(pwm_2, 200);
        digitalWrite(dir_2, HIGH);
        
        
          Serial.println("Turn LEFT");
    }
  //brake
    else if (state == 83) {
        digitalWrite(pwm_1, LOW); 
        digitalWrite(pwm_2, LOW); 
        digitalWrite(dir_1, LOW);
        digitalWrite(dir_2, LOW);
        
          Serial.println("STOP!");
         
        
        
    }
    //turn right
    else if (state == 82) {
         analogWrite(pwm_1,200); 
        digitalWrite(dir_1, HIGH); 
        analogWrite(pwm_2,80);
        digitalWrite(dir_2, HIGH);
        
          Serial.println("Turn RIGHT");
          
        
       
       
    }
    //Reverse
    else if (state == 66) {
        digitalWrite(pwm_1, HIGH);
        digitalWrite(pwm_2, HIGH); 
        digitalWrite(dir_1, LOW);
        digitalWrite(dir_2, LOW);
        
          Serial.println("Reverse!");
          delay(5);
         
        
    }
     

}


