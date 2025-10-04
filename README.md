# Nissan-BP5362-radio-Bluetooth-mod
Add bluetooth functionality to a somewhat old radio, also known as Nissan MMR CD-G or 7 645 362 318

Firstly, this is the area you want to focus on:

![20251004_142443087](https://github.com/user-attachments/assets/e2f96a77-8f7f-4f07-900f-809cf1cc6a1c)

Replace the 1.8k resistors with 10 Ohm ones, and remove the filter caps.

![20251004_142514003](https://github.com/user-attachments/assets/2079f631-5e85-4750-a19b-5fafb7595560)

In this radio model, the telephone input goes to PIN 59 and 57 of the Blaupunkt ASIC. (The schematic is for the CD30)

<img width="1692" height="1130" alt="image" src="https://github.com/user-attachments/assets/807a4cb1-acb3-4205-a352-51e285506731" />

Wire up your [MH-MX18](https://www.aliexpress.com/i/1005006917065649.html) bluetooth module, you will need the audio channels, power and mute:

<img width="1000" height="1000" alt="image" src="https://github.com/user-attachments/assets/ab7041ae-919c-46e4-bc0b-a4ef208fcacf" />

Use a copper ring terminal or something else, and build a 5v regulator on it using a 7805 or something similar. The output of this connects directly to the bluetooth module, I've used a 22uF 35V tantalum cap on the input and 10uF tantalum on the output. Put the ring part under the frame, the PCB has exposed vias with solder, this will provide ground.

![20251004_150155031](https://github.com/user-attachments/assets/d4d77533-9b49-4cca-8962-bd36cc220e3a)

The inputs from the ISO connector on the back of the radio go to an amplifier with some amount of gain, and then the output of that amplifier goes to both inputs on the ASIC. Next to the amplifier is a footprint for another amplifier, which will be used to connect the Bluetooth module's outputs. The ASIC inputs have series capacitors.

![20251004_143940151](https://github.com/user-attachments/assets/fed0f334-0e5a-49b8-9ca1-df0a924c7694)

When MUTE is low on the back of the radio, it automatically switches the inputs of the ASIC to those we wired up. However, while a track change is in progress, no audio plays, and the module will pull MUTE high which is 3.3V, same for the radio so no level shifting is required. This is rather annoying, so a delay circuit will provide enough time to keep the radio in phone mode. These values worked for me; if you experience problems, increase the capacitor's or the 470k resistor's value. The diode I used is a generic schottky.

[The circuit](https://tinyurl.com/25b7keyt):

<img width="1128" height="474" alt="image" src="https://github.com/user-attachments/assets/a1dc43e4-01b6-4cb5-8ff3-33f9ada3287a" />

MUTE goes to a 2.2k resistor on the PCB just below the area that we worked on, build the circuit around this and connect MUTE from the module.

![20251004_162243817](https://github.com/user-attachments/assets/ccc7152b-67d5-4471-bb1d-bab981c66125)

With this done everything should be ready to test, if all is well, use hotglue and SpaceTape™ (kapton) to secure the wires and components.

![20251004_163451064](https://github.com/user-attachments/assets/9edb858b-853d-4522-82af-4f1e8db5ded5)

Happy modding!
