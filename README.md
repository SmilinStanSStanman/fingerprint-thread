This is a step-by-step guide for a Fingerprint all-in-one project working with Thread. It is inspired by [this video from Domotica per Tutti](https://www.youtube.com/watch?v=EEh26tGFiz4)

**<ins>[REQUIRED MATERIALS]</ins>**

1.- ESP32-C6

2.- R503 Fingerprint reader

**<ins>[WIRING DIAGRAM]</ins>**

[WIRING DIAGRAM](docs/ESQUEMA-FINGERPRINT.jpg)

I have kept the external LED and the buzzer from the original Adonno project in the code, but since I don’t use them, I have not included them in the wiring diagram. If you want to install them, you can see how to wire them in Adonno’s project.

The ESP32-C6 must be flashed with [this YAML](fingerprint-thread.yaml) in ESPHome. The program is prepared for the ESP32 to connect to a Thread network.

**<ins>[HOW TO USE THE FINGERPRINT]</ins>**

In Home Assistant go to: Developer tools >>> Actions

To add fingerprints: esphome.tagreader_fingerprint_thread_enroll

To cancel adding fingerprints process: esphome.tagreader_fingerprint_thread_cancel_enroll

To delete a single fingerprint: esphome.tagreader_fingerprint_thread_delete

To delete all fingerprints: esphome.tagreader_fingerprint_thread_delete_all

**<ins>[ADDITIONAL TIP]</ins>**

In my setup, I need to keep the ESP32 at a certain distance from the PN532 and the fingerprint sensor (between 40-50cm). I had problems with the NFC. I couldn’t get the PN532 and the ESP32 to communicate properly. In my case, this was due to the cable length. I solved it by adding a 4.7 kΩ pull-up resistor between the ESP32's 3.3 V pin and the ESP32 GPIO pins where the PN532's SDA and SCL are connected. You can find these resistors [HERE](https://www.amazon.es/dp/B0CL6NSS45?th=1) (non-affiliated link)

![PULL-UP](docs/pull-up.jpg)
