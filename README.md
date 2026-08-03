# Acre

A farm tycoon that keeps growing while you are away.

**Play:** https://rahulatrkm.github.io/acre/

Plant and harvest, raise animals, run a mill and a bakery, and work through 24
levels. Free, no download, no account, no timers you can pay to skip.

## What it is

You start with a patch of dirt and a handful of wheat seed. Wheat feeds
chickens, chickens lay eggs, eggs and flour make cake, and cake pays for the
land that lets you do all of it faster. Each of the 24 levels asks for a
delivery you cannot quite make yet, so you go and build the thing that makes it
possible.

Crops keep growing when the tab is closed. Come back after a few hours and
there is a harvest waiting, capped so that leaving for a week is not better
than leaving for an evening.

Everything is saved in your browser. Nothing is uploaded and there is nothing
to sign up for.

## How it is drawn

There are no image files. Every crop, animal and building is drawn as SVG
generated from a seed, so a wheat field at one growth stage is literally
computed from the stage number. That keeps the whole game a single HTML file
and means it loads instantly on a bad connection.

## Tests

```bash
node acre.test.mjs      # 86 assertions
```

The suite runs the real page against a stubbed DOM and drives the economy,
growth timing, offline accumulation, level goals, save/load round-trips and the
redraw budget.

That last one is worth a note, because the first version of it was worthless.
It compared two freestanding objects and asserted they were equal — both were
zero, so it passed no matter what the game did. It now counts real writes to the
stubbed DOM: 861 on the first frame, **0** across sixty idle frames, and 1 when
a single field changes. That is the difference between a test that measures
something and a test that just looks like it does.

## Run locally

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## License

MIT.
