# APB_RAL
Protected SystemVerilog RTL for an APB-based memory with a dedicated RAL interface. The design is encrypted using Verilog `pragma protect` and can be compiled and simulated like standard RTL. Internal logic must not be modified. Verify the design using two independent agents: one APB agent and one RAL agent through the exposed interfaces.
