# 4x4x4 LED Cube using Arduino Uno

## Overview

This project involves building a **4x4x4 LED cube** controlled by an **Arduino Uno**. The cube consists of 64 LEDs arranged in 4 layers of 16 LEDs each. Using multiplexing techniques and Arduino programming, you can create stunning 3D light patterns and animations.

---

## Features

* 4x4x4 LED cube structure
* Multiple 3D animations (e.g., wave, rain, blinking)
* Arduino-controlled with easy-to-modify code
* Educational project for learning:

  * Multiplexing
  * Arduino programming
  * Electronics and circuit design

---

## Components Required

* **64 LEDs** (preferably 5mm, same color or RGB optional)
* **Arduino Uno**
* **16 x 220Ω resistors** (for columns)
* **4 x NPN transistors** (e.g., BC547 or 2N2222 for layers)
* **Connecting wires**
* **Breadboard or PCB**
* **Soldering kit** (if permanent build)

---

## Circuit Diagram

The cube uses **layer multiplexing**:

* Each **layer** is controlled by a transistor.
* Each **column** has a resistor connected to an Arduino digital pin.
* Only one layer is powered at a time while the respective columns are driven to create patterns.

```
(You can add an image of your circuit diagram here)
```

**Pin Connections Example:**

| Arduino Pin | Connection               |
| ----------- | ------------------------ |
| 2-9         | Columns (LED anodes)     |
| 10-13       | Layers (via transistors) |

> Note: Adjust pins according to your wiring.

---

## Assembly Instructions

1. **Prepare LEDs:**

   * Bend and arrange LEDs into layers.
   * Ensure cathodes of each layer are connected together.
2. **Stack Layers:**

   * Connect each layer with spacers to form the 3D cube.
3. **Wire Columns:**

   * Connect anodes of LEDs vertically to form columns.
4. **Connect to Arduino:**

   * Connect columns through resistors to Arduino digital pins.
   * Connect layers via transistors.
5. **Power the Circuit:**

   * Ensure correct power supply (Arduino 5V).

---

## Arduino Code

Here’s a basic structure for your cube:

```cpp
#define LAYER1 10
#define LAYER2 11
#define LAYER3 12
#define LAYER4 13

int columns[] = {2,3,4,5,6,7,8,9};

void setup() {
  for(int i=0; i<4; i++) pinMode(LAYER1+i, OUTPUT);
  for(int i=0; i<8; i++) pinMode(columns[i], OUTPUT);
}

void loop() {
  // Example: light up all LEDs layer by layer
  for(int i=0; i<4; i++){
    digitalWrite(LAYER1+i, HIGH);
    for(int j=0; j<8; j++){
      digitalWrite(columns[j], HIGH);
    }
    delay(100);
    for(int j=0; j<8; j++){
      digitalWrite(columns[j], LOW);
    }
    digitalWrite(LAYER1+i, LOW);
  }
}
```

> You can create advanced patterns using arrays and nested loops.

---

## Animations Ideas

* Blinking cube
* Waves moving through layers
* Random LED flashes (rain effect)
* 3D rotating patterns

---

## Troubleshooting

* **LEDs not lighting:** Check connections, resistors, and transistors.
* **Only one layer lights up:** Ensure multiplexing code cycles through layers quickly.
* **Arduino overheating:** Check for short circuits or wrong wiring.

---

## References

* Arduino official documentation: [https://www.arduino.cc](https://www.arduino.cc)
* Tutorials on 4x4x4 LED cube: [Instructables LED Cube Projects](https://www.instructables.com)

