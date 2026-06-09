# Awesome Bogominers [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of clients for [bogosort](https://bogo.swapjs.dev/) — the
> "crowd-compute on a 24/7 stream" project where everyone shuffles a deck of
> 25 cards as fast as possible, hunts for the luckiest permutation, and reports
> the best ones back to the mothership. 🃏

Bogosort runs entirely in the browser via WebGPU, but a cottage industry of
native clients has sprung up to squeeze more shuffles-per-second out of CPUs
and GPUs than a browser tab ever could. This list tracks them — grouped by
language, with what hardware each one can drive and what kind of interface it
puts in front of you.

Got one that's missing? PRs are very welcome — see [Contributing](#contributing).

## Contents

- [The Official Site](#the-official-site)
- [Rust](#rust)
- [C / C++](#c--c)
- [Contributing](#contributing)
- [Legend](#legend)

---

## The Official Site

| Project | Backend | Interface | Platform | License |
|---|---|---|---|---|
| [**bogosort**](https://bogo.swapjs.dev/) — the official site & one of the "official" way to contribute. Browser-based, WebGPU-accelerated, with accounts, leaderboards, badges/XP, and an adjustable intensity slider (tiny → max). | WebGPU | 🌐 Web (browser) | Anywhere WebGPU runs | — |

## Rust

| Project | Backends | Interface | Platform | License | Notes |
|---|---|---|---|---|---|
| [**bogominer**](https://gitlab.com/ttomcat/bogominer) — the official native client, developed by tomcat with swap. | CPU · GPU (planned) | GUI | Windows · macOS · Linux | MIT | 🚧 Early development — not yet ready for use. |
| [**bogo-gpu**](https://github.com/Wateristic/bogo-gpu) — GPU-focused worker with triple-buffered CUDA kernel dispatch, xoshiro128++ RNG, and a CPU-only Rayon fallback. Config saved to the OS-standard path on first run. | CPU (Rayon) · NVIDIA (CUDA) · AMD (HIP/ROCm) | ⌨️ CLI | Linux · Windows · macOS | — | No Vulkan support; CUDA is the default feature. Tuning guide in the README for matching `gpu_blocks`/`gpu_chunk_size` to your specific GPU. |
| [**bogoforge**](https://github.com/mnhttn-cafe/bogoforge) — community client with an AVX-512-vectorized CPU kernel (xoshiro128++ + Fisher-Yates, hand-rolled with `std::simd`) and a built-in performance-stats TUI. | CPU · NVIDIA (CUDA) · AMD (HIP/ROCm) · Vulkan | 📺 TUI | Linux · Windows · macOS | GPL-2.0 | Picks backends via Cargo feature flags (`cuda`/`hip`/`vk`); CPU path is hand-tuned for modern AVX-512 hardware (e.g. Zen 5) and degrades gracefully without it. |

## C / C++

| Project | Backends | Interface | Platform | License | Notes |
|---|---|---|---|---|---|
| [**bogo-rig**](https://github.com/xoshiro128/bogo-rig) — WebSocket client (`bogowsclient`) with selectable acceleration backends and tunable worker count / chunk size. | CPU (default) · NVIDIA (CUDA) · AMD (HIP) · Vulkan | ⌨️ CLI | 🐧 Linux (native) · Windows via WSL2 | MIT | Mostly C (80%), with C++/HIP/CUDA glue for the GPU backends. Run as `./bogowsclient --uuid ... --code ... --nickname ... --workers ... --chunk-size ...`. |

---

## Contributing

Found a client that isn't here? Please open a PR! To keep the list useful and
consistent:

1. **Add your entry** to the table for its language (create a new `##`
   section if it's the first entry in that language — keep sections
   alphabetical).
2. **Use this format** for the project cell:
   ```md
   [**name**](link) — one short, factual sentence about what makes it notable.
   ```
3. **Fill in every column** as accurately as you can:
   - **Backends** — CPU, NVIDIA (CUDA), AMD (HIP/ROCm), Vulkan, WebGPU, OpenCL, etc. List all that apply.
   - **Interface** — see the [legend](#legend) for the icon shorthand (CLI, TUI, GUI, Web, headless/daemon...).
   - **Platform** — OS support (Linux, Windows, macOS, browser, ...). Note WSL/emulation caveats explicitly.
   - **License** — the SPDX identifier if you can find one (`MIT`, `GPL-2.0`, `Apache-2.0`, ...), or `—` if unlicensed/unclear.
   - **Notes** *(optional)* — anything a miner would want to know before trying it: maturity/maintenance status, standout features, known gotchas (⚠️), setup quirks.
4. **Be honest about rough edges.** If a project is unmaintained, broken, or
   requires a janky setup, say so — that's exactly the kind of thing this list
   should help people avoid wasting time on.
5. Run [`awesome-lint`](https://github.com/sindresorhus/awesome-lint) locally
   if you can (`npx awesome-lint`) — CI will run it on your PR regardless.

Don't have all the details? Submit what you've got — entries can always be
filled in later (mark unknowns as `TBD`).

## Legend

| Icon | Meaning |
|---|---|
| ⌨️ | CLI — command-line / headless |
| 📺 | TUI — terminal UI |
| 🖥️ | GUI — desktop graphical app |
| 🌐 | Web — runs in-browser |
| ⚠️ | Heads up — see the notes column before using |

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the contributors to this list have waived
all copyright and related/neighboring rights to it under
[CC0](LICENSE). The listed projects each carry their own licenses — check
their repos before you go redistributing anything.
