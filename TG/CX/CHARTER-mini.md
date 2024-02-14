# Composable Extensions (CX) Task Group Charter

RISC-V reserves the custom-\* opcode space, enabling anyone to create new
custom extensions and their software libraries.  However, composition of
multiple extensions is unobtainable because RISC-V custom extensions are
unmanaged, lacking standards or uniformity.  This impairs extension reuse due
to conflicting opcodes or incompatible means of extension discovery,
versioning, state management, etc, ultimately leading to fragmented ecosystems
with disjoint solution silos.

By expanding the custom instruction opcode space to a nearly inexhaustible
supply of 32b opcodes, this opcode space can also be shared by future RVI ISA
extensions. This will solve the problem of limited capacity remaining within
the 32b opcode space.

The Composable Extensions (CX) Task Group(s) will specify ISA extensions
(within the Custom Opcode space), software (API, ABI) and hardware interfaces.
This will enable harmonious, robust and conflict-free composition of multiple
independently authored composable custom extensions, alongside legacy custom
instructions or extensions, in one RISC-V system. Multiple harts will be able
to share the same physical hardware module that implements one or more CX
instances.

To do this, CX will multiplex the custom opcode space and adopt common software
and hardware interop interfaces.  The CX specification will be guided by and
consider the impact of these design tenets: composability, conflict-freedom,
decentralization, stable binaries, composable and reusable hardware modules,
uniformity (of scope, naming, discovery, versioning, error signaling, state
context management, access control), frugality, security, and longevity.  In
particular, this should be done without a central management authority.

### Deliverables

The output of the TG is expected to include:
1. CX Multiplexing
1. CX State Contexts, including Supervisor/User modes
1. CX C-API, C++-API, and Runtime System
1. (optional) CX Hardware Interface

### Acceptance criteria

A proof-of-concept implementing each deliverable will involve multiple hart(s) x
extension(s) x extension librar(y/ies) x OS combinations.  

## Exclusions

Not every arbitrary custom extension can be a composable extension.  In
particular, the first release of CX will likely support only unprivileged
computational instructions. In particular, control-flow instructions will
likely be excluded.

Load/store instructions that operate on main memory, while important, add a
level of complexity that may require it to be deferred until a successive
release.  Similarly, dynamic reconfiguration of the attached CX logic, an
important capability of FPGAs that implement SoftCPUs, may also be deferred.

The CX TG is focused on the minimum viable standards *enabling*
practical composition of extensions and software. Further standards
for infrastructure and tooling e.g. for CX packages, debug, profile,
formal specification of CX interface contracts, CX library metadata,
and tools, are _out of scope_.

## Collaborations

CX multiplexing reduces the opcode and CSR impact of such extensions to zero,
extending the life of the 32b encodings.  The CX framework will enable many
unpriv computational extension TGs, e.g. the Matrix extensions.  

Interaction with a unified Discovery mechanism is important for forwards
compatability and versioning.

### Overlaps (probably many, more TBD)

* CX discovery API may overlap uniform discovery TG

## History

In 2019, the RISC-V Foundation FPGA soft processor SIG members, determined
to advance RISC-V as the preeminent ecosystem for FPGA SoCs, committed to
"Propose extensions ... to enable interoperable RISC-V FPGA platforms
and applications". SIG members set out to define standards by which
FPGAs' extensible RISC-V cores might enable a marketplace of reusable
and composable custom extensions and libraries. Through 2019-2022,
members met to define the *minimum viable set* of interop interfaces
culminating in the
[Draft Proposed RISC-V Composable Custom Extensions Specification](https://raw.githubusercontent.com/grayresearch/CX/main/spec/spec.pdf),
now proposed as a starting point for RVI CX TG work.
