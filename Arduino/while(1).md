# while (1) trick

when i encounter this it means it's a fail condition that i can't exit from unless i physically reset the board 

it's a simple exit condition that signals an error 


example 
```c
unsigned long start_time = 0;
unsigned long end_time = 0;

#define test_type byte
test_type x = 1;
test_type y = 2;
test_type z = 3;

void setup() 
{
  Serial.begin(57600);
  Serial.println("SparkFun datatype demo.");
  Serial.println("Addition with bytes: x+y=z");
  Serial.print("x=");
  Serial.println(x);
  Serial.print("y=");
  Serial.println(y);
}

void loop() 
{
  start_time = micros();
  z=x+y;
  end_time = micros();
  Serial.print("z=");
  Serial.println(z);
  Serial.print("Start time: ");
  Serial.println(start_time);
  Serial.print("End time: ");
  Serial.println(end_time);
  Serial.print("Elapsed time: ");
  Serial.println(end_time - start_time);
  while(1);  
}
```

There is no way to stop program. Running is endless

Your loop() function will exute once, an then keep evaluating while (1) endlessly.  
You can move your code in the setup() function and keep an empty loop() function with the same result


### Tags
#arduino 
#Cool_trick 