# Generated edge-e3 RTL

`edge_e3enc.v` and `edge_e3enc_sram.v` contain only obfuscated private edge-e3 RTL.
`edge_rv64_public.fl` lists the unchanged open RV64 RTL. Use `edge_e3enc_mixed.fl` for the complete design, or combine the private RTL with target-specific SRAM models/replacements for FPGA/OpenROAD.

Generate from the repository root with:

```sh
cmake --build build/cmake-harness --target edge_e3_obfuscate
```

FPGA/Yosys can consume the mixed list and select its `_yosys.v` SRAM variants:

```sh
synth/run_yosys.sh edge_core_top xilinx src/edge-e3enc/edge_e3enc_mixed.fl
```

OpenROAD can consume the same list; its runner substitutes central `*_openroad.v` blackboxes for matching SRAM/cache-array entries.
