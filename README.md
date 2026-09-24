# Generated edge-e3 RTL

`edge_e3enc.v` and `edge_e3enc_sram.v` contain the obfuscated private product RTL selected from `src/edge-e3`, `src/edge-asic`.
`edge32_public.fl` lists unchanged open RTL from `src/edge-32`. Use `edge_e3enc_mixed.fl` for the complete design, or combine the private RTL with target-specific SRAM models/replacements for FPGA/OpenROAD.

The obfuscated product RTL is distributed under the license in `LICENSE.md`.

Generate from the repository root with:

```sh
python3 tools/package_obfuscated_rtl.py
```

FPGA/Yosys can consume the mixed list and select its `_yosys.v` SRAM variants:

```sh
synth/run_yosys.sh edge_core_edge32_top xilinx src/edge-e3enc/edge_e3enc_mixed.fl
```

OpenROAD can consume the same list; its runner substitutes central `*_openroad.v` blackboxes for matching SRAM/cache-array entries.
