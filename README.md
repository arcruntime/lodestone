# Lodestone

**Ear training that explains itself.**

A relative-pitch ear trainer for musicians who want to recognise intervals by feeling, not by counting semitones — and who want to know why an interval feels the way it does, not just whether they got it right.

**Status: first draft, still in development.** The three modes work end to end; interaction and copy are still being tuned against real playtesting.

Live at [lodestone-55o.pages.dev/app/](https://lodestone-55o.pages.dev/app/).

---

## The problem

Most ear-training apps teach the same way: play two notes, show a grid of interval names, mark the answer red or green. That trains recall of a label, not the skill musicians actually use in the moment — recognising an interval by its character before you'd have time to count it. And when you get it wrong, you learn nothing about *why* — which intervals you're actually confusing, or whether the confusion is physical (the notes genuinely beat against each other) or learned (your ear expects a resolution that isn't musically "wrong," just different).

## The insight

Every interval has a measurable identity along three separate axes, and collapsing them into one vague "sounds off" is where most confusion hides:

- **Roughness** — physical beating between the two notes' overtones, audible to any listener regardless of musical background.
- **Tonal pull** — learned expectation from Western melodic convention. Real, useful, and explicitly *not* acoustics — a claim the app states in the same breath as the measurement, not just once in a footnote.
- **Fusion** — how much the two notes' overtone series line up, computed from real equal-tempered frequencies rather than approximated.

Keeping those three apart, and showing the arithmetic behind each one, is the product's actual bet: that a tool willing to show its work — and say when a measurement doesn't apply — teaches better than one that just scores you.

## What shipped (v1)

**Drill.** A twelve-node wheel arranged by circle of fifths, playing a sustained tonic drone with a single test note against it — never a chord, so there's one thing to listen for. The wheel *is* the answer surface — tap the node that matches what you heard. No feedback words, no dials, no visible scheduler: just the interval name and its semitone count after you answer. A Leitner spaced-repetition scheduler runs underneath, weighting toward what you get wrong and what's overdue, invisibly. Degree subsets (single degree, a handful, all major, all minor, everything) keep a first session from being twelve unfamiliar targets at once.

**Study.** Free exploration, no scoring. Every degree gets its own card: an editable feeling-word field (seeded with a suggestion, yours to overwrite), the roughness/fusion dials, a three-trace waveform view (root, interval, and their sum with the beat envelope drawn over it) with a sweep control that moves the interval outward from unison so you can watch — and hear — flat becomes shimmer becomes grind, and the harmonic-alignment comb showing exactly which overtones coincide. Every explanation sits behind a closed-by-default toggle; tonal pull gets a visualisation-free note instead of a chart, because charting a cultural expectation as if it were a waveform would be a false claim.

**Progress.** Reviewed after a session, never during one. A windowed trend (last 10, 25, or 100 sessions) showing starting accuracy, current accuracy, and the delta — or, honestly, a note that there isn't enough data yet to read a trend, rather than a delta computed from three data points and presented as if it meant something. Accuracy by degree, weakest first, and a full 12×12 confusion matrix, because "you're at 80%" is much less useful than "you're at 80% and it's always ♭2 you mistake for 2."

**The visual system.** Colour is data, not decoration: each of the twelve degrees gets a hue positioned by circle-of-fifths distance, not chromatic order, so colour distance encodes harmonic distance — the palette teaches while it decorates. The hue origin is chosen so the tonic and the tritone (the two harmonically furthest-apart degrees) land on the one colour axis that survives red-green colour blindness. Light mode is primary — the category defaults to dark, so a pale instrument-panel surface differentiates on sight — and dark mode ships at equal quality, following system preference with a manual override.

## What's next

The long-term differentiator is audio ML, not more content: sung-response pitch tracking with cents deviation and time-to-stability, melody extraction from real recordings so practice stops being a separate activity from listening, and confusion-matrix-driven modelling that predicts errors instead of just scheduling around them after the fact. Native wrapping is deferred until retention data says it's worth the review-cycle cost — web first, on purpose.

## In this repo

```
app/            the app — single self-contained HTML file, no build step, no dependencies
app/tokens.json the design system's source of truth: every colour, size, and spacing value
experiments/    absolute-pitch-lab, a separate screener parked out of v1's scope (see its own README)
```

The app is one file on purpose: open `app/index.html` in a browser and it runs, no install, no server, no build step.

## License

MIT — see [LICENSE](LICENSE).
