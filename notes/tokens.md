# Token prediction table (Status: behind - Week 1 Tue + Wed.)
Tool: platform.openai.com/tokenizer (GPT-5.x tokenizer; Claude's differs, same patterns)

| # | String | Predicted | Actual | Reason for the gap |
|---|--------|-----------|--------|--------------------|
| 1 | The cat sat on the mat. | 6 | 7 | Missed the full stop (its own token). Spaces attach to the next word, so they don't add tokens. |
| 2 | unbelievably | 3 | 3 | Correct. |
| 3 | antidisestablishmentarianism | 5 | 6 | BPE splits by frequency, not meaning: starts from bytes and merges the most common pairs, so chunks don't follow word parts. |
| 4 | 1234567 | 3 | 3 | Correct. Digits are grouped in fixed chunks, not seen one by one. |
| 5 | Le chat est sur le tapis. | 10 | 7 | Common languages like French cost close to English. Less-represented scripts like Arabic cost more (fewer merges, plus 2 bytes per letter in UTF-8). |
| 6 | const total = books.length; | 10 | 6 | `.length` is one token because it's extremely common in code, so BPE merged it. Spaces attach to the next word. |
| 7 | 📚📖✨ | 7 | 5 | Within 2. |
| 8 | Hello␣␣␣␣␣world (5 spaces) | 7 | 3 | ______ |

## Pattern
I overestimated every time: the vocabulary is large, so common text merges into bigger chunks than I expected.
Status: on track          ← or: Status: behind - Week 1 Tue: temperature and sampling

## Week 1, Mon (caught up Wed morning)
- Learned: BPE merges the most frequent pairs, so common English and code are cheap; rarer languages and scripts cost more tokens.
- Confused: <your words>