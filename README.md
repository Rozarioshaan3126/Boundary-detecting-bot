
#define trigPin1 4           // Trig Pin Of HC-SR04
#define echoPin1 5        // Echo Pin Of HC-SR04
#define trigPin2 6           // Trig Pin Of HC-SR04
#define echoPin2 7        // Echo Pin Of HC-SR04
#define MLa 8                   //left motor 1st pin
#define MLb 9                  //left motor 2nd pin
#define MRa 10               //right motor 1st pin
#define MRb 11               //right motor 2nd pin
long duration1, distance1, duration2, distance2 ;

void setup() {
  Serial.begin(9600);
  pinMode(MLa, OUTPUT);     // Set Motor Pins As O/P
  pinMode(MLb, OUTPUT);
  pinMode(MRa, OUTPUT);
  pinMode(MRb, OUTPUT);
  pinMode(trigPin1, OUTPUT);       // Set Trig Pin As O/P To Transmit Waves
  pinMode(echoPin1, INPUT);        //Set Echo Pin As I/P To Receive Reflected Waves
  pinMode(trigPin2, OUTPUT);       // Set Trig Pin As O/P To Transmit Waves
  pinMode(echoPin2, INPUT);        //Set Echo Pin As I/P To Receive Reflected Waves
  }
  
void loop() 
{
  Serial.begin(9600);
  digitalWrite(trigPin1, LOW);
  delayMicroseconds(2);   
  digitalWrite(trigPin1, HIGH);       // Transmit Waves For 10us
  delayMicroseconds(10);
  duration1 = pulseIn(echoPin1, HIGH);        // Receive Reflected Waves
  distance1 = duration1 / 58.2;                       // Get Distance
  Serial.println(distance1);
  delay(5); 
  
  
  if (distance1 < 10 )               // Condition For Absence Of Obstacle            
  {
    digitalWrite(MRb, HIGH);       // Move Forward
    digitalWrite(MRa, LOW);
    digitalWrite(MLb, HIGH);                                
    digitalWrite(MLa, LOW);   
                                                       
  }
  else if (distance1>15)            // Condition For Presence Of Obstacle
  {
    digitalWrite(MRb, LOW);     //Stop                
    digitalWrite(MRa, LOW);
    digitalWrite(MLb, LOW);                                
    digitalWrite(MLa, LOW);
    delay(5);
    
  
    digitalWrite(MRb, LOW);     // Move Backward             
    digitalWrite(MRa, HIGH);
    digitalWrite(MLb, LOW);                                
    digitalWrite(MLa, HIGH);
    delay(500);
    digitalWrite(MRb, LOW);        //Stop                
    digitalWrite(MRa, LOW);
    digitalWrite(MLb, LOW);                                
    digitalWrite(MLa, LOW);  
    delay(100);  
    digitalWrite(MRb, HIGH);     // Move Left     
    digitalWrite(MRa, LOW);   
    digitalWrite(MLa, LOW);                                 
    digitalWrite(MLb, LOW);  
    delay(500);
  }

digitalWrite(trigPin2, LOW);
  delayMicroseconds(2);   
  digitalWrite(trigPin2, HIGH);       // Transmit Waves For 10us
  delayMicroseconds(10);
  duration2 = pulseIn(echoPin2, HIGH);        // Receive Reflected Waves
  distance2 = duration2 / 58.2;                       // Get Distance
Serial.println(distance2);
  delay(5);



 if (distance2 < 10  )               // Condition For Absence Of Obstacle            
  {
    digitalWrite(MRb, HIGH);       // Move Forward
    digitalWrite(MRa, LOW);
    digitalWrite(MLb, HIGH);                                
    digitalWrite(MLa, LOW);   
                                                       
  }
  else if (distance2>15 )            // Condition For Presence Of Obstacle
  {
    digitalWrite(MRb, LOW);     //Stop                
    digitalWrite(MRa, LOW);
    digitalWrite(MLb, LOW);                                
    digitalWrite(MLa, LOW);
    delay(10);
    
  
    digitalWrite(MRb, LOW);     // Move Backward             
    digitalWrite(MRa, HIGH);
    digitalWrite(MLb, LOW);                                
    digitalWrite(MLa, HIGH);
    delay(500);
    digitalWrite(MRb, LOW);        //Stop                
    digitalWrite(MRa, LOW);
    digitalWrite(MLb, LOW);                                
    digitalWrite(MLa, LOW);  
    delay(100);  
    digitalWrite(MRb, HIGH);     // Move Left     
    digitalWrite(MRa, LOW);   
    digitalWrite(MLa, LOW);                                 
    digitalWrite(MLb, LOW);  
    delay(500);



 
    
  
  }
}
