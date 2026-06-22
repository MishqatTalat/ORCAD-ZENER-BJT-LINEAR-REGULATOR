# OrCAD PSpice Simulation: Zener-Referenced BJT Linear Voltage Regulator

This repository presents a complete transient simulation and waveform analysis of a linear DC voltage regulator circuit designed and verified using OrCAD PSpice. 

## Circuit Topology & Specifications
The circuit steps down and stabilizes a $12\text{V}_\text{peak}$, $50\text{ Hz}$ AC input into a clean, regulated smooth DC voltage across a $470\ \Omega$ load resistor ($RL1$).

* **Input:** $12\text{V}_\text{peak}$ AC, $50\text{ Hz}$
* **Rectification:** Full-Wave Diode Bridge Rectifier (`Dbreak`)
* **Filtering:** High-capacity $2200\ \mu\text{F}$ Electrolytic Capacitor ($C1$)
* **Voltage Reference:** $1\text{N}750$ Zener Diode ($D16$) creating a stable reference voltage baseline
* **Pass Transistor:** $Q2\text{N}2222$ NPN BJT configuring a series-pass regulator to handle load current configuration

---

## Empirical Verification & Waveform Analysis

### Stage 1: AC Input Characteristics
The primary source delivers a standard sinusoidal wave swinging between $\pm 12\text{V}$.
* **Schematic Node:** ![AC Input Probe]<img width="975" height="394" alt="schmetic_ac_probe" src="https://github.com/user-attachments/assets/d8a3c0cb-91a5-477c-b02a-7a0285512ba6" />

* **Transient Response:**
![AC Input Waveform]<img width="975" height="366" alt="ac_waveform" src="https://github.com/user-attachments/assets/36274c0d-6abf-4951-b4c5-4d61f9fe199b" />


### Stage 2: Full-Wave Rectification & Filtering (Pulsating DC)
The bridge rectifier flips the negative half-cycles, while the $2200\ \mu\text{F}$ capacitor filters the heavy ripples, maintaining a high average DC value with negligible voltage droop.
* **Schematic Node:**
![Pulsating DC Probe]<img width="970" height="399" alt="schmetic_pulsating_dc" src="https://github.com/user-attachments/assets/d5ef22da-d053-4873-b9b7-325c1b781219" />

* **Transient Response:**
![Pulsating DC Waveform]<img width="975" height="373" alt="dc_pulsating_waveform" src="https://github.com/user-attachments/assets/7cf7044e-1c52-4d1c-b983-e64826b35f7a" />


### Stage 3: Zener Voltage Reference Stabilizing
The Zener diode breaks down in reverse-bias mode, locking the base voltage of the BJT pass transistor to a solid, stable horizontal line at approximately $4.7\text{V}$.
* **Schematic Node:**
![Zener Reference Probe]<img width="975" height="405" alt="_schematiczener_reference_voltage" src="https://github.com/user-attachments/assets/c985732d-a2d6-42e6-8a78-f302fea3d8b7" />

* **Transient Response:**
![Zener Reference Waveform]<img width="975" height="383" alt="zener_reference_voltage_waveform" src="https://github.com/user-attachments/assets/d92ea71f-30fa-4ace-a798-a4e7f6f8f45c" />


### Stage 4: Final Regulated Load Voltage Output
The NPN transistor acts as an emitter-follower. The output tracked at $RL1$ is perfectly flat and regulated at approximately $4.0\text{V}$ ($V_\text{out} = V_\text{Zener} - V_\text{be}$), completely isolated from the main input ripple frequencies.
* **Schematic Node:**
![Load Output Probe]<img width="975" height="405" alt="svhmetic_load_output" src="https://github.com/user-attachments/assets/ceae07af-2c47-4d4a-a366-823cb0c6ffad" />

* **Transient Response:**
![Regulated Output Waveform]<img width="975" height="414" alt="load_output_waveform" src="https://github.com/user-attachments/assets/e5b30172-5d64-4fce-a5c9-8bbb6a24a119" />


---

## Technical Conclusion
The transient analysis verifies that even with a fluctuating AC primary source, the circuit successfully filters raw ripple structures and locks the output load voltage to a constant $4\text{V}$ line, satisfying key linear regulation objectives.
