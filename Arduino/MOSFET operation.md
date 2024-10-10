# How to drive a mosfet with arduino 

1. gate goes to the pin 
2. continuity with body means it's the source (la fonte principale ed è sempre più alta)!
3. the remaining pin is the drain (immagine lo scarico che va alla MASSA (terra) )!

- Imagine the the two pins _are_ the power source to your target be it (LED, Motor, etc). 
- it's just an intermediary between the power source (battery) and the item driven. 
- it comes AFTER the driven item before the power source
>[!NOTE]
>power source(+) --> driven led --> Mosfet --> Ground

![[Mosfet With powerLed.jpeg]]

Example code 
you can simply apply a PWM signal to the Gate and the MOSFEt will be driven accordingly 

```C

```

questo [qui](https://wolles-elektronikkiste.de/en/the-mosfet-as-switch) è una eccellente fonte per saperne di più

### Gate resistor 

I always use gate resistors, but typically 1.0 to 10 ohms for high speed PWM, 10 to 100 ohms for low speed applications. The 150 ohm value is rather high for a PWM gate drive. How fast is the PWM in Hz? A 150 ohm resistor will result in a slow FET transition from on to off and vice-versa. If it is a very small FET w/ low gate charge, I suppose 150 ohms could work. Just curious.

Placement of the pull down resistor on the gate 

![[Pasted image 20231117113803.png]]

- why does this happen  ? 
because the gate source acts like a capacitor !!

![[Pasted image 20231117113854.png]]

[Lettura aggiuntiva](https://www.build-electronic-circuits.com/mosfet-gate-resistor/)
anche [qui](https://www.microtype.io/designing-power-mosfet-circuits/)


### Tags
#arduino 
#MOSFET 
#electronics