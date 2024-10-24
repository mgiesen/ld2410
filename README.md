# LD2410
A lightweight library for the LD2410 sensor, enabling easy UART communication and efficient monitoring of sensor output with minimal overhead.

> [!WARNING]  
> This library is currently under development and not yet ready for production use

## Features

- Optional UART communication with configurable baud rates
- Optional Output pin observation using an interrupt callback
- Optional Debugging support via serial output
- Ring buffer implementation for efficient serial data handling

## Pinout
![ld2410_pinout.png](/readme/ld2410_pinout.png)

## Documentation

- [Manual EN](docu/Manual.pdf)
- [Serial Communication EN](docu/Serial%20Communication.pdf)

## Usage

**Initialization**  
```cpp
LD2410 sensor;
```

**Debugging**  
```cpp
Serial.begin(115200);

sensor.useDebug(Serial);
```

**UART Communication**  
```cpp
setup() 
{
    sensor.beginUART(rxPin, txPin, Serial2, 256000); 
}

loop() 
{
    sensor.processUART();
}
```

**Output Observation**  
```cpp
setup() 
{
    void outputCallback(bool presenceDetected) {}

    sensor.beginOutputObservation(pin, outputCallback);
}
```
