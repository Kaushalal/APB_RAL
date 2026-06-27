# APB_RAL
Protected SystemVerilog RTL for an APB-based memory with a dedicated RAL interface. The design is encrypted using Verilog `pragma protect` and can be compiled and simulated like standard RTL. Internal logic must not be modified. Verify the design using two independent agents: one APB agent and one RAL agent through the exposed interfaces.
# APB RAL Memory RTL (Protected Version)

## Overview

This repository contains a protected RTL implementation of an APB-based memory module integrated with a Register Abstraction Layer (RAL).

The RTL has been encrypted using Verilog `pragma protect` directives to protect the internal implementation while allowing normal simulation and integration into verification environments.

## Features

* APB Slave Interface
* Dedicated RAL Register Interface
* Independent APB and RAL clock domains
* Configurable memory depth
* Protected RTL source
* Compatible with standard simulation flows

---

## Top-Level Module

```
apb_ral_top
```

This module provides:

* APB Slave Interface
* RAL Register Interface

No internal implementation details are exposed.

---

## Interfaces

### APB Interface

| Signal  | Description        |
| ------- | ------------------ |
| PCLK    | APB Clock          |
| PRESETn | Active-Low Reset   |
| PSEL    | Slave Select       |
| PENABLE | APB Enable         |
| PADDR   | Address Bus        |
| PWRITE  | Read/Write Control |
| PWDATA  | Write Data         |
| PSTRB   | Byte Enable        |
| PRDATA  | Read Data          |
| PREADY  | Ready Response     |
| PSLVERR | Error Response     |

---

### RAL Interface

| Signal    | Description           |
| --------- | --------------------- |
| RAL_CLK   | RAL Clock             |
| RAL_RESET | Active-High Reset     |
| ral_addr  | Register Address      |
| ral_wr_en | Register Write Enable |
| ral_wdata | Register Write Data   |
| ral_rdata | Register Read Data    |

---

## RAL Register Map

| Address | Register    | Access       |
| ------- | ----------- | ------------ |
| 0x400   | INTR        | Read / Write |
| 0x404   | CONTROL     | Read / Write |
| 0x408   | IO_ADDRESS  | Read / Write |
| 0x40C   | MEM_ADDRESS | Read / Write |

---

## Verification

The RTL is intended to be verified using two independent verification agents.

| Agent     | Purpose                                      |
| --------- | -------------------------------------------- |
| APB Agent | Generates and monitors APB transactions      |
| RAL Agent | Generates and monitors RAL register accesses |

Both agents operate on the same DUT through their respective interfaces.

---

## Protected RTL

The RTL source is protected using Verilog encryption.

* Internal implementation is not visible.
* Internal logic must not be modified.
* Use the module exactly as a standard RTL.
* Verification should be performed only through the public interfaces.

---

## Simulation

Instantiate the protected RTL in your testbench and compile it together with your verification environment.

Example:

```text
RTL
 ↓
Compile
 ↓
Simulation
 ↓
APB Agent + RAL Agent
 
```

---

## Notes

* No internal implementation details are provided.
* The external interfaces remain fully accessible.
* The protected RTL behaves identically to an unprotected RTL during simulation.
* The register map above is the supported programming interface for the RAL block.

---

## License

This repository contains protected intellectual property (IP).

Modification, reverse engineering, or redistribution of the protected RTL is prohibited unless explicitly authorized by the IP owner.
