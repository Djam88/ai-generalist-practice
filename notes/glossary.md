# Glossary

- **token:** a piece of text (a whole word, part of a word, a space or punctuation), taken from a fixed vocabulary built before training by merging the most frequent pairs; before the model sees it, the tokeniser turns it into a token ID (a number).
- **token ID:** the number label for a token, its position in the vocabulary list (e.g. `.length` → 13,402); the same token always has the same ID. It's a label, not a score.
- **tokeniser:** the program that splits text into tokens using its vocabulary and converts each into a token ID on the way in; on the way out, it converts the model's chosen token IDs back into text.
- **next-token prediction:** given all the tokens so far, the model outputs a probability distribution over its whole vocabulary for the next token. It is the training task in pretraining, and, repeated with sampling, the way the model generates text.
- **logit:** a raw score the model outputs for every token in its vocabulary as a candidate for the next token; not yet a probability (it can be negative, and they don't sum to 100%), before temperature division and softmax.
- **temperature:** a number that the logits are divided by before softmax. Low T (below 1) makes the distribution sharper (the top token gets nearly all the balls, so output is predictable); high T (above 1) makes it flatter (other tokens get more balls, so output is more varied); T=1 leaves it unaltered.
- **sampling:** picking one token at random from the probability distribution, weighted by each token's probability, so likely tokens win most often but unlikely ones can still be picked (like a Loto draw where likelier tokens have more balls in the drum, and the drum is refilled for every new token: https://www.youtube.com/watch?v=EHIf9N6mI1A).

## Still to define
- probability distribution:
- parameters:
- pretraining:
- fine-tuning:
- RLHF:
- inference:
- greedy decoding:
- top P (nucleus sampling):
- MoE (Mixture-of-Experts):