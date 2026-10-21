# OpenCode Free Models Catalog

A reference for the free models available in the OpenCode catalog (OpenCode Zen
provider).

Every model listed here costs **$0 per million input tokens**, **$0 per million
output tokens** and **$0 per million cached read tokens**. Each one calls tools.

The table gives the served limits, the effort variants, the modalities and the
main use case for each model.

> Catalog read on 2026-10-21. The free roster rotates often. Verify the list with
> `opencode models` or the OpenCode Zen documentation before you depend on a
> model.

---

## The 10 free models

| Model | Context / max output | Input modalities | Effort variants | Weights | Released | Best for |
|---|---|---|---|---|---|---|
| **MiniMax M3.1 Flash Free**<br>`minimax-m3.1-flash-free` | 1M / 131K | text, image, video | low, medium, high, xhigh, max | open | 2026-10-19 | Frontier coding and long-horizon agents. Newest model in the list. |
| **Nemotron 3.5 Super VL Free**<br>`nemotron-3.5-super-vl-free` | 1M / 131K | text, image | none, minimal, low, medium, high, xhigh | open | 2026-10-15 | Visual agents: screenshots, PDFs, charts, GUI work. |
| **Beam Free**<br>`beam-free` | 1M / 131K | text | low, medium, high, xhigh, max | open | 2026-10-05 | The hardest coding and agentic work. Token-efficient reasoning. |
| **LongCat 2.5 Preview Free**<br>`longcat-2.5-preview-free` | 1M / 131K | text, image | toggle only | closed | 2026-09-25 | Cheap long-context analysis. Preview model, no published benchmarks. |
| **MiMo-V2.6-Flash Free**<br>`mimo-v2.6-flash-free` | 200K / 32K | text, image, audio, video | none | open | 2026-09-22 | The only model here that reads audio and video. |
| **DeepSeek V4.1 Flash Free**<br>`deepseek-v4.1-flash-free` | 200K / 32K | text, image | low, high, max | open | 2026-09-10 | Lean agentic coding. Top open-weight model on Code Migration. |
| **GLM-5.3-Flash Free**<br>`glm-5.3-flash-free` | 200K / 32K | text, image, video, pdf | low, high, max | open | 2026-08-26 | Frontend work. Visual self-verification of layouts. |
| **Nemotron 3.5 Lightning Free**<br>`nemotron-3.5-lightning-free` | 256K / 256K | text | none | open | 2026-08-11 | Fast, cheap subagent work. Smallest model here (30B-A3B). |
| **Big Pickle**<br>`big-pickle` | 200K / 32K | text | none | closed | 2025-10-17 | Everyday coding. Stealth model. Tightest output budget. |
| **Nemotron 3 Ultra Free**<br>`nemotron-3-ultra-free` | 1M / 128K | text | none | open | 2026-06-04 | Maximum open-weight reasoning accuracy. |

The default model listing shows 8 entries. Two more appear only with the full
listing (`all: true`): **MiniMax M3.1 Flash Free** and **Nemotron 3.5 Lightning
Free**.

---

## Effort variants

Only 3 models support the full ladder of effort tiers.

| Model | Effort ladder |
|---|---|
| MiniMax M3.1 Flash | low, medium, high, xhigh, max |
| Beam | low, medium, high, xhigh, max |
| Nemotron 3.5 Super VL | none, minimal, low, medium, high, xhigh |
| DeepSeek V4.1 Flash | low, high, max |
| GLM-5.3-Flash | low, high, max |
| LongCat 2.5 Preview | toggle only |
| MiMo-V2.6-Flash | none. Reasoning is always on. |
| Nemotron 3.5 Lightning | none. Reasoning is always on. |
| Big Pickle | none. Reasoning is always on. |
| Nemotron 3 Ultra | none. Reasoning is always on. |

### How to pair a tier with a model

These tiers follow the effort levels `low`, `medium`, `high`, `xhigh` and `max`.

| Tier | Model | Reason |
|---|---|---|
| `low`, `medium` | Nemotron 3.5 Lightning | 256K context, no effort knob, built for throughput. |
| `high` (default) | Big Pickle or DeepSeek V4.1 Flash | Big Pickle has no effort control. `high` is its normal behavior. |
| `xhigh` | Beam at `xhigh` | Beam is trained from effort 8. Lower values have no effect. |
| `max` | Beam or MiniMax M3.1 Flash | Both support the top of the ladder. |
| `ultracode` | MiniMax M3.1 Flash or Nemotron 3.5 Super VL | 1M context and a wide fan-out budget. |

**Note on `max` with DeepSeek V4.1 and GLM-5.3.** Those two have a 3-step
ladder. Use `max` only for a task that is genuinely hard. The top step costs the
most and leaves no middle ground.

---

## What to know before you route work here

### The output ceiling is the real limit

Six of the ten models cap output at 32K: Big Pickle, MiMo-V2.6-Flash, DeepSeek
V4.1, GLM-5.3-Flash, LongCat 2.5 and MiniMax on some endpoints. Big Pickle has
only 160K usable input out of its 200K window.

If a task generates many files in one turn, the output ceiling stops the work
before the context window does. Split the task into turns, or move to Beam or
MiniMax, which allow 131K of output.

### Free means training

Most free models use your data to train the model.

Models listed as **Training**:

- Big Pickle
- MiMo V2.5
- MiMo V2.6 Flash
- Muse Spark 1.2 and 1.3 Contributor
- Jev 1.13 Free
- Exo Free

Models with **zero retention**:

- LongCat 2.5 Preview Free
- Space Bunny Free (no longer offered)

**Do not send confidential or client code through a training-tier model.** Use a
paid model for private work.

### The roster rotates

These models still appear in some caches but report as unavailable or deprecated:

- `step-5-preview-free`
- `space-bunny-free`
- `mimo-v2.5-free`
- `ling-3.0-flash-fin-free`
- `muse-spark-1.2-contributor-free`
- `nemotron-3-super-free`

A local model cache can be one month behind the live catalog. Refresh it before
you depend on a model.

---

## Two limits of this data

### Context numbers are endpoint-specific

The vendor's native context window is not always the window that Zen serves.

| Model | Native context | Served by Zen |
|---|---|---|
| DeepSeek V4.1 Flash | 1M | 200K |
| MiMo-V2.6-Flash | 1M | 200K |
| GLM-5.3-Flash | 1M | 200K |
| LongCat 2.5 Preview | 1M | 1M |

The table above uses the Zen-served numbers, because those are the numbers that
apply to a request through OpenCode.

### Big Pickle has no confirmed identity

Big Pickle is a stealth model. Community reports point to GLM-4.6, but no
provider confirms it. Big Pickle is **not** GLM-5.3-Flash.

Treat any lesson from prompt tuning on Big Pickle as provisional. Test the same
prompt again after the model changes.

---

## Source

- Model catalog: `opencode models` (OpenCode Zen provider)
- Effort and context definitions: OpenCode Zen documentation
- Vendor specifications: the model cards and product pages of each vendor

## License

MIT
