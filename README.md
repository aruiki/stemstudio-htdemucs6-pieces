# stemstudio-htdemucs6-pieces

HT-Demucs 6-stem (`htdemucs_6s`, Défossez et al., Meta AI, MIT) as an ONNX graph split into 32 pieces at module boundaries, packed into one bundle and stored as two parts (GitHub's per-file limit). Used by StemStudio to run 6-stem separation in the browser on phones and laptops: the pieces run one at a time, so peak memory is far lower than with the single graph, and the output is identical (max difference 0.0).

Concatenate the parts in order to get `htdemucs_6s.pieces.bin` (143,411,590 bytes, sha256 `4df9bbbeb6c14cdd91ef7f242c0277a0098912526a9fcb8d5dbc21486d410773`).

Bundle format: `"SSPC1\0\0\0"` | u32le header length | JSON header (per-piece inputs, outputs, offset, length) | piece bytes. Built with `web/scripts/split-model.py` in the StemStudio repository.
