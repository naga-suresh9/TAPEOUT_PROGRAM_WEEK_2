# 📘 Week 2 – BabySoC Theory: SoC Fundamentals & Functional Modelling

## 🤔 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** is like a **mini-computer on a single chip**. Instead of having separate CPU, memory, and peripherals on different boards, an SoC **combines all these components** into one silicon chip.

💡 **Benefits of SoCs:**

* 🔹 Smaller size → fits in smartphones, IoT devices
* 🔹 Lower power consumption → energy-efficient
* 🔹 Faster communication → components directly connected

An SoC usually contains:

1. **💻 CPU (Processor)** – executes instructions and controls operations
2. **🧠 Memory** – stores data temporarily (RAM) or permanently (ROM/Flash)
3. **📡 Peripherals** – interfaces to communicate with outside world (UART, SPI, GPIO)
4. **🔗 Interconnect** – buses or network connecting CPU, memory, and peripherals

---

## 🍼 Why BabySoC Exists

**BabySoC** is a **simplified SoC model for learning**. It focuses on the essential components of a real SoC without overwhelming complexity.

* Lets learners **observe CPU operation, memory access, and peripheral interaction**
* Focuses on **signal flow and module communication**
* Makes it easy to **simulate and debug** before moving to real hardware

Think of it as a **training ground for understanding SoC design concepts**.

---

## ⚙️ Functional Modelling: What & Why

**Functional modelling** is the process of **simulating the SoC at a high level** to verify its behavior **before creating physical hardware**.

🔹 **Key purposes:**

1. ✅ **Verify functionality** – does the CPU generate correct outputs? Does the DAC convert properly?
2. 🛑 **Catch errors early** – fix mistakes in design flow, saving time and cost
3. 🔄 **Faster iterations** – easy to change logic at this stage without touching real hardware

**Tools used:**

* **Icarus Verilog (`iverilog`)** → compile and simulate Verilog RTL
* **GTKWave** → view signal waveforms for analysis

---

## 🧩 How BabySoC Works

* **CPU (`rvmyth`)** → executes instructions and produces a digital output
* **PLL (`avsdpll`)** → generates a stable clock to synchronize CPU and other modules
* **DAC (`avsddac`)** → converts CPU digital output to analog signals

Signal flow example:

```
[CPU (rvmyth)] --> digital output --> [DAC (avsddac)] --> analog OUT
         ^
         |
       clock (from PLL)
```

* The **testbench** initializes signals and clocks, then simulates this flow
* **Waveforms (.vcd)** are captured to observe reset, clock, and dataflow

---

## 🎯 Key Learning Outcomes from Theory

By understanding BabySoC theory:

* You can **explain what a SoC is and how it works**
* You know the **purpose of each module** (CPU, PLL, DAC)
* You understand **functional modelling** and why simulation is critical
* You are ready to **perform hands-on simulations** for Week 2

---

✅ **Analogy:** BabySoC is like a **mini music player chip**:

* CPU → Composer deciding the notes
* PLL → Metronome keeping the timing correct
* DAC → Speaker converting notes to sound

Simulation ensures the **music plays correctly** before building the real chip.

---
