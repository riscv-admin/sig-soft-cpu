# SoftCPU SIG Gap Analysis

## GAP: Composable Extensions

1. Creation of TGs for CX
   * draft the TG Charter
2. remote CSRs and how they interact with context state (check interactions with AIA, register-addressable CSRs). Are they shared per CXU, per context, per hart, or not shared?
3. opcode allocation -- maybe reserve a block for traditional custom use (not used by CX)
4. state contexts are separate from harts (standard or optional?)
5. speculative issue of stateful instructions
6. main memory read/write consistency
   * interleaving of accesses
   * logic channel (through cache? direct to mem? etc)
7. expanding beyond custom[012] opcode blocks; granularity
8. acknowledge V1 limits: integer regfile, no shared context; consider fpreg, vecreg, ...
9. PULP stream semantic registers
10. register pairs, eg {X[i], X[i+1]}
    
## GAP: Other

1. Analyze New vs Existing Platforms & Profiles in the context of SoftCPUs
2. Analyze Debug Spec in the context of SoftCPUs
3. Identify missing/needed/desired standards/commonalities needed for cross-vendor compatability of RISC-V SoftCPUs
   * Board Dev Kits
   * Computer system IP (AXI, UART, etc)
   * IRQs
   * EDA/Composition tools
   * IP-XACT
