# 🌟 Week 2 – BabySoC Fundamentals & Functional Modelling 🚀

## 📘 Part 1 – Theory: SoC Fundamentals

### 🤔 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** is a **mini-computer on a single chip**, integrating CPU, memory, peripherals, and interconnects.

💡 **Benefits of SoCs:**

* 🔹 Smaller size → fits in smartphones, IoT devices
* 🔹 Lower power consumption → energy-efficient
* 🔹 Faster communication → components directly connected

Typical components:

* 💻 **CPU** – executes instructions and controls operations
* 🧠 **Memory** – RAM for temporary, ROM/Flash for permanent storage
* 📡 **Peripherals** – UART, SPI, GPIO, timers
* 🔗 **Interconnect** – buses or network connecting CPU, memory, and peripherals

---

### 🍼 Why BabySoC Exists

* Simplified **learning model** of SoC
* Helps observe **CPU operation, memory access, and peripheral interaction**
* Focuses on **signal flow and module communication**
* Easy to **simulate and debug** before hardware implementation

---

### ⚙️ Functional Modelling: What & Why

Functional modelling simulates the SoC at a **high abstraction level** to verify behavior before building hardware.

🔹 **Purposes:**

* ✅ Verify functionality (CPU & DAC output correctness)
* 🛑 Catch errors early (save time and cost)
* 🔄 Faster iterations (modify logic easily)

**Tools:**

* 🖥️ **Icarus Verilog (iverilog)** – Compile and simulate RTL
* 📊 **GTKWave** – View waveforms for analysis

---

### 🧩 How BabySoC Works

* **CPU (`rvmyth`)** → executes instructions, generates digital output
* **PLL (`avsdpll`)** → provides a stable clock
* **DAC (`avsddac`)** → converts digital output to analog

```
[CPU (rvmyth)] --> digital output --> [DAC (avsddac)] --> analog OUT
         ^
         |
       clock (from PLL)
```

* **Testbench** initializes signals & clocks, dumps `.vcd` waveforms
* Observe **reset**, **clock**, and **dataflow** signals

---

### 🎯 Key Learning Outcomes

* Explain **SoC architecture** and module roles
* Understand **functional modelling** importance
* Ready for hands-on **simulation & waveform analysis**

✅ **Analogy:** BabySoC = mini music player

* CPU → Composer deciding the notes
* PLL → Metronome keeping timing correct
* DAC → Speaker converting digital notes to sound

---

## 🌟 Part 2 – Hands-on Functional Modelling

### 🎯 Objective

Gain practical experience simulating BabySoC using:

* 🖥️ **Icarus Verilog** → compile RTL modules
* 📊 **GTKWave** → view and analyze waveforms
* 🧪 **Testbench** → verify functional behavior

---

### 🛠️ Step-by-Step Procedure

<details>
<summary>📂 Click to expand steps</summary>

1️⃣ **Setup Project Directory**

```bash
cd ~/New/
git clone https://github.com/hemanthkumardm/SFAL-VSD-SoC-Journey.git
cd "SFAL-VSD-SoC-Journey/12. VSDBabySoC Project"
mkdir -p output/pre_synth_sim output/post_synth_sim
```

2️⃣ **Pre-Synthesis Compilation & Simulation**

```bash
iverilog -o output/pre_synth_sim/pre_synth_sim.out -DPRE_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v src/module/vsdbabysoc.v
cd output/pre_synth_sim
./pre_synth_sim.out
gtkwave pre_synth_sim.vcd
```

3️⃣ **Post-Synthesis Compilation & Simulation**

```bash
iverilog -o output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v output/synthesized/vsdbabysoc.synth.v
cd output/post_synth_sim
./post_synth_sim.out
gtkwave post_synth_sim.vcd
```

4️⃣ **Analyze Waveforms**

* Reset operation ⏱️
* Clock behavior 🕒
* Dataflow between modules 🔀

5️⃣ **Document Observations**

* Take **screenshots**
* Write **short explanations** per screenshot

</details>

---

### ⚠️ Common Errors & Fixes

<details>
<summary>❗ Click to see all errors & solutions</summary>

**Error:** Module redefinition

* **Fix:** Include each module only once in compilation

**Error:** VCD file missing

* **Fix:** Ensure `$dumpfile` and `$dumpvars` are in testbench

**Error:** Wrong include paths

* **Fix:** Use correct `-I src/include -I src/module` paths

</details>

---

### 📊 Workflow Diagram

```
+----------------+       ⚡ compile       +----------------+
| testbench.v    | --------------------> |  rvmyth.out    |
| rvmyth.v       |                       | (simulation)   |
+----------------+ <------------------- +----------------+
         |      run simulation & dump waveform
         v
+----------------+
|  rvmyth.vcd    |
| (VCD waveform) |
+----------------+
         |
         v
+----------------+
| GTKWave Viewer |
| waveform analysis |
+----------------+
```

---

### 📂 Project Structure

```text
Week2/
├── src/module/rvmyth.v         🖥️ RTL Design
├── src/module/testbench.v      🧪 Testbench
├── src/include/my_macros.vh    📝 Macros & definitions
├── output/pre_synth_sim/rvmyth.vcd  💾 VCD waveform
├── screenshots/
│   ├── reset.png               ⏱️ Reset waveform
│   ├── clock.png               🕒 Clock waveform
│   └── dataflow.png            🔀 Dataflow waveform
├── week2_simulation_log.txt     📄 Simulation logs
└── README.md                   📘 Documentation
```

---

### 📸 Simulation Results

1️⃣ **Reset & Clock Operation ⏱️**

* ✅ Reset asserted at start
* ✅ Clock drives modules correctly
* ✅ Signals transition as expected

2️⃣ **Dataflow Between Modules 🔀**

* ✅ Program counter & data signals toggle correctly
* ✅ Data moves accurately between modules
* ✅ Confirms functional correctness



---

### 🏆 Outcome 🎉

* 💡 Learned SoC design fundamentals
* 🖥️ Compiled & simulated BabySoC modules successfully
* 📊 Verified functional behavior using waveforms
* 📝 Documented reset, clock, and dataflow

---

### 📦 Deliverables

* 📄 `week2_simulation_log.txt` → simulation logs
* 🖼️ Waveform screenshots (reset, clock, dataflow)
* 📝 Short explanation per screenshot

---

✅ This README combines **theory + functional modelling + simulation documentation** into **one complete Week 2 report**, ready for GitHub submission.

---

If you want, I can **also make a version with collapsible screenshots + fancy emojis per section** to make it look even more **interactive and impressive** for your repo.

Do you want me to do that?
