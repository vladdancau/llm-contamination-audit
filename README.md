# Checkpoint-Trajectory Contamination Audit

Detects whether a benchmark item was plausibly seen during a model's
pretraining by sweeping its **full public checkpoint trajectory**, not just
the final weights. The audit is wrapped in a cryptographic trail
(scope commitment, Merkle root over checkpoints, Ed25519 signature) so it is
pre-registered and non-repudiable.

## Contents

- **[`contamination_audit.ipynb`](contamination_audit.ipynb)** — the audit.
  Builds up the method cell by cell (memorization heuristic, commit-then-reveal,
  Merkle commitment, checkpoint hashing, signing, orchestration) and ends with a
  real run on Pythia over ARC-Easy (plausible leakage) and GPQA (negative control).
- **[`llm_contamination_audit.pdf`](llm_contamination_audit.pdf)** — compiled
  report: the notebook with narrative and results rendered for reading.

## Running

```
pip install -r requirements.txt
jupyter notebook contamination_audit.ipynb
```

The final section additionally needs `transformers`, `datasets`, and
`huggingface_hub`, plus a Hugging Face login to pull the Pythia checkpoints.

## References

- Jia et al., *Proof-of-Learning: Definitions and Practice* (2021). https://arxiv.org/abs/2103.05633
- Fang et al., *Proof-of-Learning is Currently More Broken Than You Think* (2022). https://arxiv.org/abs/2208.03567
- Choi, Shavit & Duvenaud, *Tools for Verifying Neural Models' Training Data* (2023). https://arxiv.org/abs/2307.00682
- Arun et al., *Verde: Verification via Refereed Delegation for Machine Learning Programs* (2025). https://arxiv.org/abs/2502.19405
- Biderman et al., *Pythia: A Suite for Analyzing Large Language Models Across Training and Scaling* (2023). https://arxiv.org/abs/2304.01373
