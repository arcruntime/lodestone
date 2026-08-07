# Absolute Pitch Lab

An absolute-pitch screener and trainer, built while scoping Lodestone and kept here as a separate experiment rather than folded into the main product.

**Why it's separate.** Lodestone teaches relative pitch — the relationship between notes, which is trainable at any age. Absolute pitch (naming a note with no reference) is a different skill with a much narrower trainable window in adults, and conflating the two in one product would misrepresent what either one can promise. Scoping it out kept the core product honest about what it teaches.

**What it does.** A screener designed to resist the usual false positives: randomised octave and timbre per trial, a memory-wiping scramble between questions, latency capture, and no feedback while it's running — the conditions that separate genuine absolute pitch from someone quietly counting up from a remembered reference note. It then offers a landmark-based training track that starts from one anchor note and expands outward, for the partial/learned pitch memory that adults can build even without true AP.

Results are read against a stated baseline (chance is 8.3% across twelve pitch classes) and interpreted by pattern, not just score — genuine AP tends to be fast and stable across timbre and register with octave-level errors; learned pitch memory tends to be slower, piano- and white-key-biased, with errors clustering a semitone or two away. That distinction — and the willingness to say which one a given result looks like — is the interesting part of this artifact.

Single self-contained file, no build step, no dependencies. Open `index.html` and it runs.
