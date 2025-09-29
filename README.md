# 🌟 Week 2 – BabySoC Functional Modelling & Simulation 🚀

## 🎯 Objective

Gain hands-on experience in **SoC fundamentals** by performing **functional modelling** of the BabySoC using:

* 🖥️ **Icarus Verilog** – Compile RTL modules
* 📊 **GTKWave** – Analyze simulation waveforms
* 🧪 **Testbench** – Verify functional behavior

---

## 🛠️ Step-by-Step Procedure 🔹

<details>
<summary>📂 Click to expand steps</summary>

1. **📥 Clone the Project**

   ```bash
   git clone https://github.com/manili/VSDBabySoC.git
   cd VSDBabySoC/src/module
   ```

2. **⚡ Compile RTL & Testbench**

   ```bash
   iverilog -o output/pre_synth_sim/rvmyth.out rvmyth.v testbench.v
   ```

3. **▶️ Run Simulation**

   ```bash
   ./output/pre_synth_sim/rvmyth.out
   ```

4. **💾 Generate VCD Waveform**

   * Ensure `$dumpfile` and `$dumpvars` present in `testbench.v`

5. **👀 Open Waveforms in GTKWave**

   ```bash
   gtkwave output/pre_synth_sim/rvmyth.vcd
   ```

6. **🔄 Observe Signals**

   * ⏱️ Clock and reset operations
   * 🔀 Dataflow between modules
   * 📡 Inter-module communication

7. **📝 Document Observations**
   Capture screenshots and note key behaviors.

</details>

---

## ⚠️ Common Errors & Fixes 🛠️

<details>
<summary>❗ Click to see all errors & solutions</summary>

### 🚫 TL-Verilog Not Found

```bash
tlverilog --version
tlverilog: command not found
```

* 🔍 Reason: TL-Verilog not installed (not needed for Week 2)
* ✅ Fix: Use `iverilog` + `gtkwave`

---

### 🚫 GTKWave Not Opening

* 🔍 Reason: Tried opening inside Yosys shell
* ✅ Fix: Exit shell, run:

```bash
gtkwave rvmyth.vcd
```

---

### 🚫 `.vcd` File Missing

* 🔍 Reason: `$dumpfile` or `$dumpvars` missing in testbench
* ✅ Fix: Add dump commands, re-run simulation

---

### 🚫 Compilation Errors

* 🔍 Reason: Syntax errors or module port mismatch
* ✅ Fix: Check semicolons, module ports, and signal widths

</details>

---

## 📊 Workflow Diagram 🔄

```text
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

## 📂 Project Structure 🗂️

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

## 📸 Simulation Results

### 1️⃣ Reset & Clock Operation ⏱️


* ✅ Reset asserted at start
* ✅ Clock drives modules after reset
* ✅ Signals transition as expected

---

### 2️⃣ Dataflow Between Modules 🔀
 

* ✅ Program counter & data signals toggle correctly
* ✅ Data moves accurately between modules
* ✅ Confirms functional correctness

---

## 🏆 Outcome 🎉

* 💡 Learned **SoC design fundamentals**
* 🖥️ Successfully **compiled & simulated** BabySoC modules
* 📊 Verified **functional behavior** with waveform analysis
* 📝 Documented **reset, clock, and dataflow** with screenshots

---

## 📦 Deliverables

* 📄 `week2_simulation_log.txt` – simulation logs
* 🖼️ Waveform screenshots (reset, clock, dataflow)
* 📝 Step-wise explanation per screenshot

---
