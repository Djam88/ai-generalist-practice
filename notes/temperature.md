
# Temperature and sampling

**Key sentence:** Lowering T stretches the gaps between the logits (the raw scores), so after softmax the top token gets more of the probability and every other token gets less.

**Order of operations (once per token):**
1. The model produces a logit (raw score) for every token in its vocabulary.
2. The logits are divided by T. A small T stretches the gaps; a large T shrinks them.
3. Softmax turns the scores into probabilities that add up to 100%.
4. One token is sampled from that distribution and appended, then the loop repeats.

**My numbers (logits mat 5 / rug 3 / cat 2):**
- T = 1: 84.38 / 11.42 / 4.20%
- T = 0.5: 97.96 / 1.79 / 0.24%

**Terms:**
- logit: the raw score for a token before softmax
- greedy decoding: always taking the top token (the limit as T → 0)