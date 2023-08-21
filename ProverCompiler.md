# Prover compiler

Prover compiler source code: https://gitlab.com/distributed_lab/zk-reviews/gnark-wasm-prover/
Code was forked from: https://github.com/vocdoni/gnark-prover-tinygo

Prover is a part of the *Frontend* component that is run is browser to generate a *SNARK* proof. Prover is run in **WASM** so that it can be exeuted from browser.

*How to compile gnark circuit to WASM?*

By using Go compiler:
`make compile-wasm-go-g16` for Groth16 
`make compile-wasm-go-plonk` for Plonk

By using **tinygo** (generates smaller WASM):

`make compile-wasm-tinygo-g16`
`make compile-wasm-tinygo-plonk`

Build are optimized with `wasm-opt`, so you need to make sure you have it available in your system.

*How to run prover in browser*

First step after circuit compilation is to copy JS *wrapper* that allows to execute WASM to example webpage:

If you built **WASM** with *    *:

`cp ./aux/wasm_exec_go.js ./examples/web/wasm_exec.js`

Or for **tinygo**:

`cp ./aux/wasm_exec_tinygo.js ./examples/web/wasm_exec.js`

