# Audio Demo Samples — Region-Aware Masking for Accent-Robust Cross-Lingual TTS

Listening samples accompanying the paper. Each example asks the model to speak an
**English** sentence in the voice of a **non-English reference recording**, so a good
result keeps the speaker's timbre without carrying their accent into the English.

## How to listen

**Online:** open the GitHub Pages link for this repository.

**Locally:** download or clone the repository and open `index.html` in any browser.
No server, build step, or network access is needed — the page is self-contained.

## What is here

12 examples drawn from the FLEURS evaluation set used in the paper, four per source
language (Spanish, French, Portuguese), all synthesising English:

| | |
|---|---|
| Reference prompt | the non-English recording the model is conditioned on |
| Target text | the English sentence the model must speak |
| System outputs | the same sentence from all eight systems |

Within each language, the first example is one where every system preserves the
speaker; the rest are examples where the more aggressive masking policies do not.

## Systems

| System | Masking | Pairing |
|---|---|---|
| B | — | multilingual single-language utterance baseline |
| M1 | random | random |
| M2 | two_region | random |
| M3 | part1_only, *s*~U | random |
| M4 | part1_only, *s*=1 | random |
| M5 | uniform | random |
| M5+P | uniform | ECAPA-TDNN retrieval |
| M2+P | two_region | ECAPA-TDNN retrieval |

All systems are compared at the same training budget.

## Scores shown

Each row reports values **for that specific clip**, so they differ from the averages
reported in the paper.

- **Accent** — mean listener rating, 0–5, lower is better
  (0 none, 1 very slight, 2 mild, 3 moderate, 4 strong, 5 very strong)
- **Voice changed** — share of the 20 listeners who judged the speaker completely
  different from the reference; a row is flagged when at least half did
- **UTMOS** — predicted mean opinion score for naturalness, 1–5, higher is better
- **SIM** — ECAPA-TDNN cosine similarity to the reference, −1 to 1, higher is better
- **WER** — word error rate from Whisper large-v3, lower is better

The accent and voice-changed columns come from the paper's human listening study;
UTMOS, SIM and WER are automatic metrics.
