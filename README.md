# transfylitics
Transfilytics is an interactive software tool for analysing transfer functions of analogue filters and continuous linear systems. It supports multiple input formats, automatically classifies filter behaviour, computes key frequency-response parameters, and displays Bode plots and pole-zero maps through a graphical interface.

> **Note:** The current software interface is available in Brazilian Portuguese.

---

## 📌 Overview

Transfilytics was designed for educational, academic, and technical use, supporting students, researchers, and professionals in the interpretation of linear time-invariant systems.

The application currently has two equivalent implementations:

- MATLAB version (`analisador_filtros_v4`)
- Python version (`ANALISADOR_FILTROS_V4.5`)

Both versions provide real-time numerical and graphical analysis.

<img width="1910" height="1016" alt="graphical-interface" src="https://github.com/user-attachments/assets/faf07ad1-fab9-463d-83ad-7e297a3bf434" />

---

## 🌐 Interface Language

The current graphical user interface (GUI) is available in **Brazilian Portuguese**.

Although this repository and its documentation are written in English, the menus, labels, buttons, and on-screen messages in the software are currently presented in Portuguese. This does not affect the analytical functionality of the program.

A future internationalised version with an English interface may be released in later updates.

---

## 🎯 Objectives

- Facilitate the study of transfer functions
- Automate analogue filter classification
- Calculate relevant frequency-response parameters
- Visualise magnitude, phase, and pole-zero maps
- Support teaching, laboratory activities, and engineering projects

---

## ⚙️ Features

### 🔹 System input

- Numerator and denominator coefficients
- Poles, zeros, and gain
- Symbolic expression in the variable \( s \)

### 🔹 Automatic analysis

Automatic filter classification:

- low-pass
- high-pass
- band-pass
- band-stop
- undefined type

### 🔹 Calculated parameters

- cutoff frequency (-3 dB)
- centre frequency
- bandwidth
- quality factor (Q)
- peak gain
- poles and zeros
- system order

### 🔹 Graphical visualisation

- Bode magnitude plot
- Bode phase plot
- s-plane pole-zero map

### 🔹 Additional resources

- quick examples for classical filters
- automatic frequency-range adjustment
- cutoff-frequency highlighting
- interface reset and clearing tools

### 🔹 Additional feature in the Python version

- export of plots as PNG files

---

## 🏗️ Architecture

### MATLAB

- MATLAB (R2020a or later)
- Control System Toolbox
- Interface based on native graphical components

### Python

- Python 3
- Tkinter (graphical user interface)
- NumPy, SciPy, SymPy
- Matplotlib (graphical visualisation)

---

## 🔄 Operating Workflow

1. Enter the transfer function
2. Build the mathematical model
3. Compute the frequency response
4. Determine poles and zeros
5. Automatically classify the filter
6. Display numerical and graphical results

---

## 🧠 Distinctive Features

- Implemented in both MATLAB and Python
- Flexible mathematical input formats
- Automatic filter classification
- Integrated numerical analysis and graphical visualisation
- Suitable for educational and technical applications
- Plot export in the Python version

---

## 💻 Requirements

### MATLAB
- MATLAB R2020a or later
- Control System Toolbox

### Python
- Python 3
- NumPy, SciPy, SymPy, Matplotlib
- Tkinter

---

## 📚 Application Areas

- Electrical engineering
- Electronics
- Telecommunications
- Control systems
- Signal processing
- Education

---

## 📦 Versions

- MATLAB: v4.4
- Python: v4.5

---

## 👤 Authors

- Marcel Luiz Basso  
- Chiara das Dores do Nascimento  
- Everton Granemann Souza  

---

## 📚 Citation

If this software contributes to your research, please cite it as:

Basso, M. L.; Nascimento, C. D.; Souza, E. G. (2026).  
*Transfilytics: Transfer Function Analytics for Linear Systems*.  
Educational software.  
Available at: https://github.com/everton-grs/transfilytics

---

## 🧾 Registration

Software currently under registration with the Brazilian National Institute of Industrial Property (INPI).

---

## ⚖️ Licence

To be defined (e.g. MIT License)
