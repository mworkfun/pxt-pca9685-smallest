
# micro:bit PCA9685 driver

This is an extremely generic PCA9685 driver for the BBC micro:bit and Microsoft MakeCode Editor.

Supported LED, Servo, Continuous Rotation Servo and direct manipulation of the PCA9685.

![image](img/pic1.jpg)

## Adding to Project

From within [MakeCode](https://makecode.microbit.org/) select the "Advanced" section. Click on "+ Extensions" in the "Search or enter project URL..." section enter "https://github.com/mworkfun/pxt-pca9685-smallest".

![image](img/pic2.jpg)
![image](img/pic3.jpg)

![image](img/pic4.jpg)

## Constants

### PinNum

 * Pin0
 * Pin1
 * Pin2
 * Pin3
 * Pin4
 * Pin5
 * Pin6
 * Pin7
 * Pin8
 * Pin9
 * Pin10
 * Pin11
 * Pin12
 * Pin13
 * Pin14
 * Pin15

### ServoNum

 * Servo1
 * Servo2
 * Servo3
 * Servo4
 * Servo5
 * Servo6
 * Servo7
 * Servo8
 * Servo9
 * Servo10
 * Servo11
 * Servo12
 * Servo13
 * Servo14
 * Servo15
 * Servo16

### LEDNum

 * LED1
 * LED2
 * LED3
 * LED4
 * LED5
 * LED6
 * LED7
 * LED8
 * LED9
 * LED10
 * LED11
 * LED12
 * LED13
 * LED14
 * LED15
 * LED16

## Servos

### setServoPosition(servoNum, degrees, chipAddress)

#### Options:

 * chipAddress - Address of the PCA9685 in decimal
 * servoNum - Servo number to change the position of, accepts 1 to 16
 * degrees - Degrees to move the servo to, accepts 0 to 180

### setCRServoPosition(servoNum, speed, chipAddress)

#### Options:

 * chipAddress - Address of the PCA9685 in decimal
 * speed - Direction and speed to rotate, accepts -100 to 100
 * degrees - Degrees to move the servo to, accepts 0 to 180

### setServoLimits(servoNum, minTimeCs, maxTimeCs, midTimeCs, chipAddress)

**NOTE:** If you read online you will most likely find that your servos specifications rate the min and max as milliseconds and this library requires centiseconds.  To go from milliseconds to centiseconds multiple by 10.  So 0.5 milliseconds equals 5 centiseconds, 2.5 milliseconds equals 25 centiseconds.

#### Options:

 * chipAddress - Address of the PCA9685 in decimal
 * minTimeCs - Minimum time in centiseconds for the 0 position of the servo; eg 5
 * maxTimeCs - Minimum time in centiseconds for the 180 position of the servo; eg 25
 * midTimeCs - The mid (90 degree for regular or off position if continuous rotation) for the servo, set to -1 to auto calculate; eg: 15

## LED's

### setLedDutyCycle(ledNum, dutyCycle, chipAddress)

#### Options:

 * chipAddress - Address of the PCA9685 in decimal
 * ledNum - LED number to change the position of, accepts 1 to 16
 * dutyCycle - Percentage duty cycle to light the LED with accepts 0 to 100

## Direct Pin

### setPinPulseRange(pinNum, onStep, offStep, chipAddress)

**NOTE:** Direct Pin control is done using index's 0-15 **NOT** 1-16 like the LED and Servo helpers above.

#### Options:

 * chipAddress - Address of the PCA9685 in decimal
 * pinNum - Pin number to change the duty cycle of, accepts 0-15
 * onStep - When during the frame to turn on the pin, accepts 0-4095
 * offStep - When during the frame to turn off the pin, accepts 0-4095

## General

### init(chipAddress, frequency)

Changes the chip frequency to the value passed in between 40Hz and 1000Hz then performs a soft reset on the PCA9685 and sets the output states to all of the outputs to off.  You will need to set your output values again if you decide to initialize the chip after you have set a particular output value.

### reset(chipAddress)

Maintains the existing chip frequency setup and performs a chip init, see init(chipAddress, frequency) for more details.

## Example Usage

![image](img/pic5.png)

```
let controller = 0
input.onButtonPressed(Button.A, () => {
    PCA9685.setServoPosition(PCA9685.ServoNum.Servo1, 0, controller)
    basic.showString("A")
})
input.onButtonPressed(Button.B, () => {
    PCA9685.setServoPosition(PCA9685.ServoNum.Servo1, 180, controller)
    basic.showString("B")
})
input.onButtonPressed(Button.AB, () => {
    PCA9685.setServoPosition(PCA9685.ServoNum.Servo1, 90, controller)
    basic.showString("C")
})
PCA9685.init(controller, 60)
```

## License

MIT

## Supported targets

* for PXT/microbit
(The metadata above is needed for package search.)


```package
https://github.com/mworkfun/pxt-pca9685-smallest
```
