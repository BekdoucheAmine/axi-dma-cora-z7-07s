# Direct Memory Access via High Performance AXI Slave Port

## Material

1. [Cora Z7-07S (Zynq-7000)](https://digilent.com/shop/cora-z7-zynq-7000-single-core-for-arm-fpga-soc-development/)
2. [Xilinx Design Pack 2018.3 (Vivado+SDK)](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/archive.html)

## Cloning

- Main Repository
    Be sure to use “--recursive” to include the submodules:
    ```bash
    git clone --recursive https://github.com/BekdoucheAmine/axi-dma-cora-z7-07s.git
    ```

- Sub-Module

  1. Simple Polling
        ```bash
        git clone https://github.com/BekdoucheAmine/axi-dma-sp-cora-z7-07s.git
        ```
  2. Interrupt
        ```bash
        git clone https://github.com/BekdoucheAmine/axi-dma-intr-cora-z7-07s.git
        ```
  3. Scatter-Gather
        ```bash
        git clone https://github.com/BekdoucheAmine/axi-dma-sg-cora-z7-07s.git
        ```

## Usage

### Vivado Project Setup

1. Open Vivado (the main IDE).
2. Under TCL Console.
    1. Use the cd command to navigate to the folder containing your script:
        ```tcl
        cd ../axi-dma-cora-z7-07s/*replace-with-project-folder*/hardware-src/
        ```
    2. Run the script by typing:
        ```tcl
        source script_name.tcl
        ```
3. Vivado will execute the commands and automatically open the project in the GUI.

### Xilinx SDK Project Setup

1. Launch SDK and Create a new Application Project

    1. Open Xilinx SDK. 
    2. Select `File` > `New` > `Application Project`.
    3. Under Target Hardware, click `New` and browse for the corresponding hardware under `project_name/hardware-src/*.hdf`. 
    4. Click `Finish`.
    4. Select the Operating System (`standalone`) and the Processor (`ps7_cortexa9`).
    5. Click `Finish`. This builds the Board Support Package (BSP) which contains the drivers for your specific hardware.

2. Add Your Software Source

    Add existing code:

    1. Once the project is created, locate the src folder in the SDK Explorer.
    2. Drag and drop your .c file(s) into that folder.

3. Setup `Run Configuration`
    1. Select the correct hardware for the drop down list.
    2. In Target Setup, check `Reset FPGA`, `Program FPGA`, `ps7_init`, `ps7_post_config`.
    3. In Application, check `ps7_cortexa9_0`.
    4. Click `Apply`, then `Close`.

4. Build and Run.