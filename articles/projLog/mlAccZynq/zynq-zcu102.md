# Project log in Zynq-zcu102

## ***Matrix Mul&&Add Using SDSOC***

### 05/25/2018

- ***Data Mismatch***

**Details**: computing output mismatch between arm CPU and Xilinx FPGA

**Solutions**: I set clock frequency of **data movement** is the same as computing core working frequency, it works.
