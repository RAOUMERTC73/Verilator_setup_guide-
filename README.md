# Verilator Setup Guide on Ubuntu

## Created by: Rao Muhammad Umer
### Date: 04/23/2024  During DreamBig Semiconductor Internship 

---

## 1. Installing Verilator Using Binary Release

### **Download and Extract Binary Release**
1. Download the OSS CAD Suite binary release package:
   ```sh
   wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2024-04-09/oss-cad-suite-linux-x64-20240409.tgz
   ```
2. Create a directory named "Utils" in the user's home directory:
   ```sh
   mkdir ~/Utils
   ```
3. Extract the downloaded package into the "Utils" directory:
   ```sh
   tar xzf oss-cad-suite-linux-x64-20240409.tgz -C ~/Utils
   ```

---

## 2. Verify Verilator Installation
1. Execute Verilator to verify its installation:
   ```sh
   /home/ubuntu/Utils/oss-cad-suite/bin/verilator
   ```
2. Check the version of the installed Verilator:
   ```sh
   /home/ubuntu/Utils/oss-cad-suite/bin/verilator --version
   ```

---

## 3. Update PATH Environment Variable
1. Open the `.bashrc` file for editing:
   ```sh
   nano ~/.bashrc
   ```
2. Add the Verilator binary directory to the PATH environment variable:
   ```sh
   export PATH=${PATH}:/home/ubuntu/Utils/oss-cad-suite/bin/
   ```
3. Save and close the file, then reload `.bashrc`:
   ```sh
   source ~/.bashrc
   ```
4. Verify the PATH update:
   ```sh
   echo $PATH
   ```
5. Ensure Verilator is accessible:
   ```sh
   verilator --version
   ```

---

## 4. Installing and Using GTKWave
### **Install GTKWave**
```sh
sudo apt-get install gtkwave
```

### **View Simulation Waveforms**
```sh
gtkwave <waveform_file>
```

### **Check GTKWave Version**
```sh
gtkwave --version
```

### **GTKWave Help and Documentation**
```sh
gtkwave --help
man gtkwave
```

---

## 5. Explanation of Verilator Flags
### **Commonly Used Flags:**
- `--binary`: Generates a binary executable for simulation.
- `--timing`: Enables timing-accurate simulation.
- `--cc`: Generates C++ code for the simulation.
- `--trace`: Enables waveform tracing for debugging.
- `--exe`: Generates an executable simulation file.
- `-o simulation`: Specifies the output file name for the simulation.

---

## 6. Simulating and Viewing Waveforms with Verilator and GTKWave

1. **Prepare the Design Files**
   ```sh
   cd Desktop/linux_commad/vscode/sample_test/
   ```
2. **Compile and Simulate**
   ```sh
   verilator --binary test.sv test_tb.sv --timing --trace
   ```
3. **Navigate to the Output Directory**
   ```sh
   cd ./obj_dir/
   ```
4. **Run the Simulation**
   ```sh
   ./Vtest
   ```
5. **Open GTKWave to View Waveforms**
   ```sh
   gtkwave dump.vcd
   ```

---

## 7. Simulation Time Comparison: Verilator vs. ModelSim
| Feature         | Verilator | ModelSim |
|----------------|-----------|----------|
| Logic Handling | 2-state (0,1) | 4-state (0,1,X,Z) |
| Language Support | Verilog/SystemVerilog | Verilog, VHDL |
| Performance    | Faster | Slower for large designs |
| Licensing      | Open-source | Commercial |

---

## Thank You! 🎉
