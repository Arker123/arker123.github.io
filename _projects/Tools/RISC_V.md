---
title: RISC-V Simulator
subtitle: A simulator for running RISC-V machine code.
contributors:  Arnav Kharbanda*, Yashasav Prajapati*, Gopal Bansal*
date: 2022-01-01
image: ../images/RISCV.jpg
carousels: 
  - images: 
    - image: ../images/RISCV.jpg
      desc: RISC-V Simulator

order: -50
---
Github: [Github](https://github.com/Arker123/RISC-V-Simulator)
Website: [Website](https://risc-v-simulator-sigma.vercel.app)

### RISC-V Simulator

I developed a **RISC-V simulator** using **C** and **Python** to run RISC-V machine code. The simulator includes the following features:

- **Pipelining**: I implemented pipelining to simulate different stages of instruction execution, which helps speed up the processing of instructions.
  
- **Data Forwarding**: To handle data dependencies more efficiently, I added data forwarding. This feature allows the results from earlier pipeline stages to be used directly in later stages, improving performance.

- **Cache Memory**: The simulator also supports cache memory, which speeds up memory access by storing frequently used data in faster memory, reducing delays.

### Conclusion:
Building this RISC-V simulator was a fun and rewarding project. It gave me a deeper understanding of how processors handle instructions and memory. With features like pipelining, data forwarding, and cache memory, the simulator efficiently runs RISC-V machine code and can be used for both learning and performance analysis.