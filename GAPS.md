# SoftCPU SIG Gap Analysis
    
## Gaps and Priorities 2025

1. Reboot Cache Management Operations (CMO) TG to add by-index operations for invalidate/clean/flush
1. Propose RVS, a new RISC-V Soft Processor Profile, and resolve any differences with RVM (microcontroller profile) as well as intended use cases (Linux vs Embedded)
1. Extend the MISA CSR concept to provide the runtime discovery of many SoftCPU implementation features (eg, cache configuration, optional ISA features included) that cannot be reliably encoded into static board support packages due to volatility of soft processors
1. Methods for supporting fast interrupts: AMD's vectored interrupts, shadow register file
1. Consider extending shadow register file to support fast function calls (ie, ABI and gcc/llvm)
1. Address problem of multilib requiring hundreds of precompiled variants to be prepared in advance and shipped with FPGA vendor cross-compiler toolchains. ARM has been working on this [https://github.com/llvm/llvm-project/blob/main/clang/docs/Multilib.rst](https://github.com/llvm/llvm-project/blob/main/clang/docs/Multilib.rst).
1. Any requirements or issues that get dropped from the CX TG version 1 such as speculative CX issue, memory access instructions and related issues (coherence, consistency, virtual memory, IOMMUs, CX-based caches), PULP stream semantic registers, register pairs, direct use of FP or V registers, CXU-LogicInterface, mapping P and similar extensions to CX
1. Consider a Soft Processor **Platform** definition, and the intended use case (eg Linux vs Embedded)
1. Any items from prior years not explicitly marked as **[completed]** or **[abandoned]** should be considered active with a lower priority than 2025 (but maintaining priority within their year).
1. Any items carried forward will be given a new priority. (No attempt is made to archive the item's location or prioirty assigned in prior years.)

## Gaps and Priorities 2024

1. **[completed]** CX TG creation **[issues migrated to CX TG]**
    * remote CSRs and how they interact with context state (check interactions with AIA, register-addressable CSRs). Are they shared per CXU, per context, per hart, or not shared?
    * opcode allocation -- maybe reserve a block for traditional custom use (not used by CX)
    * state contexts are separate from harts (standard or optional?)
    * speculative issue of stateful instructions
    * main memory read/write consistency
      * interleaving of accesses
      * logic channel (through cache? direct to mem? etc)
    * expanding beyond custom[012] opcode blocks; granularity
    * acknowledge V1 limits: integer regfile, no shared context; consider fpreg, vecreg, ...
    * PULP stream semantic registers
    * register pairs, eg {X[i], X[i+1]}
1. **[completed]** Explore a RISC-V Soft Processor Profile
1. **[completed]** SoftCPU Workshop
1. Review Debug and Trace specifications in the context of SoftCPUs
1. Review existing RVI specifications in the context of SoftCPUs to uncover new gaps
1. Identify missing/needed/desired standards/commonalities for cross-vendor compatability of RISC-V SoftCPUs including:
    * board support packages
    * hardware IP (AXI, UARTs, etc)
    * interrupt controllers
    * EDA/composition tools
    * IP-XACT 
1. Inventory open source SoftCPU cores and classify availability, development status, etc
