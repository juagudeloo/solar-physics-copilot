# vlm

Empty on purpose. The prototype (frozen Surya encoder, token crop and pool to 256, trainable MLP
projector, frozen Qwen3-8B) lives in `vision-language-model-surya/` and is ported here when the
first small batch of verified data exists. It is trained and evaluated on whatever verified subset
is available while more data is verified. Always report n next to every result.

Tests go in `tests/`.
