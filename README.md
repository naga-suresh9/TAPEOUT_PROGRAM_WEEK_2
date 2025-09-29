# TAPEOUT_PROGRAM_WEEK_2
# 🌟 BabySoC – Week 2 Functional Modelling 🚀

Welcome to my **Week 2 journey** on BabySoC! This task demonstrates **SoC fundamentals** and **functional simulation** of the RVMyth core using **Icarus Verilog** and **GTKWave**.  

---

## 🎯 Objective

- Understand **SoC fundamentals** 🧠  
- Perform **functional modelling** of BabySoC 💻  
- Analyze **reset, clock, and dataflow** signals using `.vcd` waveforms 📊  

---

## 🛠️ Tools Used

- 🖥️ **Icarus Verilog** → Compile Verilog RTL  
- ⚡ **vvp** → Run simulation executable  
- 👀 **GTKWave** → View waveform and analyze signals  

---

## 🔗 Workflow Overview

```text
[ rvmyth.v + testbench.v ] 
        │
        │ compile
        ▼
   [ rvmyth.out ] 
        │
        │ run simulation & dump waveform
        ▼
   [ rvmyth.vcd ] ------------------> [ GTKWave Viewer ]
````

> All signals including **reset**, **clock**, and **dataflow** are observed in GTKWave.

---

## 📂 Project Structure

```
VSDBabySoC/
├─ src/
│  ├─ module/
│  │  ├─ rvmyth.v        # 🧩 Main RVMyth RISC-V core
│  │  └─ testbench.v     # 🧪 Testbench for simulation
│  └─ include/
│     ├─ my_macros.vh       # 📌 Macro definitions
│     ├─ sandpiper_gen.vh   # 🛠️ SandPiper auto-generated headers
│     ├─ sandpiper.vh       # ⚙️ SandPiper definitions
│     ├─ sp_default.vh      # 📝 Default configs
│     └─ sp_verilog.vh      # 💡 Verilog helper functions
├─ output/
│  └─ pre_synth_sim/
│     ├─ rvmyth.out  # ⚡ Simulation executable
│     └─ rvmyth.vcd  # 📊 VCD waveform
└─ README.md
```

> Each folder/file is modularized for **simulation, analysis, and documentation**.

---

## 📝 Simulation Steps

1️⃣ **Clone the repo:**

```bash
git clone <repo-url>
cd VSDBabySoC
```

2️⃣ **Compile design & testbench:**

```bash
iverilog -I src/include -o output/pre_synth_sim/rvmyth.out src/module/rvmyth.v src/module/testbench.v
```

3️⃣ **Run simulation executable:**

```bash
vvp output/pre_synth_sim/rvmyth.out
```

4️⃣ **Open waveform in GTKWave:**

```bash
gtkwave output/pre_synth_sim/rvmyth.vcd
```

---

## 📸 Simulation Waveform

Here’s the captured waveform from **`rvmyth.vcd`**:

![BabySoC Simulation]
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/14fce871-1fab-44db-8a5a-9bab80f10660" />

**Observation:**

* 🔄 **Reset:** At the start, reset is asserted and registers initialize to 0
* ⏱️ **Clock:** After reset, clock drives the design correctly
* 🔀 **Dataflow:** Signals toggle and move across modules, confirming functional correctness

---

## ✅ Deliverables

* 📝 **Simulation logs:** `output/pre_synth_sim/rvmyth.out`
* 📊 **Waveform file:** `output/pre_synth_sim/rvmyth.vcd`
* 🖼️ **Waveform screenshot:** `images/rvmyth_vcd.png`
* ✍️ **Observations/explanations** included above

---

## 🏆 Week 2 Outcome

By completing this task:

* ✅ Learned SoC fundamentals and BabySoC architecture 🧠
* ✅ Compiled and simulated the RVMyth core successfully ⚡
* ✅ Verified reset, clock, and dataflow signals in GTKWave 👀
* ✅ Documented workflow, waveform, and observations 📸

✨ **Week 2 – BabySoC functional modelling completed!** 🎉

---

