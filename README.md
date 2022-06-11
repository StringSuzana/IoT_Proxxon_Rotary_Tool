# IoT Proxxon Rotary Tool

## Abstract

It was a lazy afternoon and we were talking what could we do with a handheld drill, specifically a rotary tool. Not just any rotary tool, but Proxxon Micromot 50/E. As you may know (probably not), the Proxxon Micromot 50/E drill doesn't have a good speed regulation. Actually it is old style of regulating RPM's by using a potentiometer and a tryac. Plus added cost of their special power supply. Which is only a transformer with a bridge rectifier and capacitor to weakly smooth the voltage. The consequence of this is that the RPM's are not accurate and also your torque is not as good as you would like. You can stall it easily and perhaps ruin your precious work. What we wanted to achieve? Proxxon Micromot 50/E, but with a twist (in [Requirements](#requirements)).

## Requirements

- Stable speed (RPM) regulation
- Power limiting
- Motor temperature monitoring
- TCP/IP connectivity
  - Access point mode
  - Station mode
- Telemetry
  - Telnet
  - Web GUI
- USB-C connector for power
- Power supply voltage negotiation
  - Quick Charge (QC)
  - USB-PD (USB Power Delivery)
  - Classic DC power supply (12V - 24V)

## Breakdown

### RPM Regulation

### PID Regulation

### PID Autotune

### Power Limiting

Using INA219 sensor we measure the current and power consumption. If the current is too high, we stop the motor. Also we limit the power to the maximum motor rated power.

### Motor Temperature Monitoring

In case of over temperature we notify the user by beeping the motor, and if the temperature is too high, we stop the motor.

### TCP/IP Connectivity

Espressif ESP32 is used as the main microcontroller. It has a built-in TCP/IP stack.

### Telemetry

Voltage, Current, Power, Temperature, RPM, Torque, and other data are sent to the data interface.

### USB-C Connector for power

Nothing special here. We could also use it for sending data and programming the microcontroller.

### Power Supply Voltage Negotiation

When using a QC or USB-PD capable power supply we negotiate the maximum voltage that can be supplied. For DC power supply we use what we can. I case that we exceed the maximum voltage of 32V we go into a protection mode.
