# Contributing to Awesome Bogominers

Thanks for helping keep this list current! Here's everything you need to know.

## Adding an entry

1. **Fork** the repo and create a branch.
2. **Add your entry** to the table for its implementation language. If no
   section exists yet for that language, create one (`## Language`) — keep
   language sections in alphabetical order.
3. **Use this format** for the project name cell:
   ```md
   [**name**](https://link-to-repo-or-homepage) — one concise sentence on what makes it notable.
   ```
4. **Fill in every column:**

   | Column | What to put |
   |---|---|
   | **Backends** | All compute backends supported: CPU, NVIDIA (CUDA), AMD (HIP/ROCm), Vulkan, WebGPU, OpenCL, … |
   | **Interface** | Use the icon + label from the [legend](README.md#legend): CLI, TUI, GUI, Web |
   | **Platform** | OS/environment support. Call out WSL/emulation caveats explicitly. |
   | **License** | SPDX identifier (`MIT`, `GPL-2.0`, `Apache-2.0`, …) or `—` if none/unclear. |
   | **Notes** | Optional — standout features, build quirks, maturity/status (🚧 WIP, ⚠️ caveat…) |

5. **Be accurate about status.** If a project is in early development, not
   yet functional, or unmaintained, say so briefly — that's useful information,
   not a slight.
6. **One entry per PR** keeps review easy.
7. Open the PR — CI runs `awesome-lint` automatically.

## What belongs here

- Any client that connects to `bogo.swapjs.dev` and participates in the
  bogosort / bogo-mining network
- Any language, any platform, any interface — CLI daemons, TUI dashboards,
  browser extensions, mobile apps, whatever exists

## What doesn't belong

- Forks with no meaningful changes from the upstream they forked
- Abandoned projects with no releases and no recent commits (>1 year) —
  unless they're historically significant or the only client of their kind
- Tools that aren't actually bogominer clients (general shuffle benchmarks,
  unrelated crypto miners, etc.)

## Updating an existing entry

Found outdated info — a project changed its license, added a new backend,
got abandoned? PRs to correct existing entries are just as welcome as new ones.
Include a brief note in the PR description explaining what changed and why.

## Questions?

Open an issue — happy to help figure out where something fits.
