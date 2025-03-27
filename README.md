# Analog-to-Digital Conversion using Pulse Code Modulation (PCM)

## Overview
This project implements an Analog-to-Digital Converter (ADC) using the Pulse Code Modulation (PCM) technique. The system converts continuous analog signals into digital bitstreams through three key processing stages: sampling, quantization, and source encoding. The implementation combines hardware components on a breadboard with software processing on an Arduino.

## Project Architecture
The PCM conversion process consists of three sequential stages:

### 1. Sampling Stage
- **Purpose**: Converts continuous analog signals into discrete-time signals
- **Implementation**: Sample and hold circuit with oscillating clock
- **Key Components**:
  - Ring Oscillator based clock circuit
  - Frequency determined by: f = 1/(2NTd)
    - N = number of inverters
    - Td = propagation time of an inverter
  - MOSFETs to control number of active inverters
  - 4×1 demultiplexer for MOSFET gate regulation

### 2. Quantization Stage
- **Purpose**: Discretizes sampled signal amplitudes into finite levels
- **Implementation**: Op-amp based comparator circuit with selectable quantization levels
- **Key Components**:
  - User-selectable quantization resolution (2, 4, 8, or 16 levels)
  - Multiplexers for voltage reference selection
  - Precision voltage dividers for reference voltage generation
  - Op-amp comparators for level determination
- **Considerations**:
  - Introduces quantization error (difference between original and quantized values)
  - Error decreases with increased number of quantization levels

### 3. Source Encoding Stage
- **Purpose**: Converts quantized levels into digital binary representation
- **Implementation**: Arduino-based processing
- **Key Components**:
  - Arduino code for level mapping
  - analogRead() function to read quantized voltage levels
  - Mapping logic to convert voltage levels to binary codes
  - Serial interface for digital bitstream output

## Hardware Requirements
- Breadboard
- Arduino board (Uno)
- Operational amplifiers
- Inverters (for clock circuit)
- MOSFETs
- 4×1 Demultiplexer
- Multiplexers
- Precision resistors for voltage dividers
- Switches for quantization level selection
- Jumper wires
- Power supply

## Software Requirements
- Arduino IDE
- Serial monitor or terminal program

## Circuit Diagrams
1. **Sampling Circuit**: Op-amps buffers along with a PMOS acting like a switch 
2. **Quantization Circuit**: Op-amp comparators with voltage dividers
3. **Level Selection**: Switch-based selection for quantization resolution
4. **Clock Circuit** :  Timer circuit built with Hex inverters 

## Setup Instructions
1. Assemble the sampling circuit on the breadboard
2. Implement the quantization circuit with selectable levels
3. Connect the quantized output to an analog input pin on the Arduino
4. Upload the provided source encoding code to the Arduino
5. Connect the analog signal source to the input of the sampling circuit
6. Monitor the digital output via the Arduino's serial interface


## Performance Considerations
- **Sampling Rate**: Determined by the oscillating clock frequency
- **Quantization Error**: Inversely proportional to the number of quantization levels
- **Resolution**: Selectable between 1-bit (2 levels) and 4-bit (16 levels)

## Future Improvements
- Implement digital-to-analog conversion for signal reconstruction
- Add error detection and correction capabilities
- Increase quantization resolution beyond 16 levels
- Add filtering to reduce aliasing effects during sampling
