# ✈️ GATE 404 — Airport OOTD Randomizer

A randomizer for the pre-flight ritual where everyone shows up at the airport in an
assigned, deeply embarrassing outfit and hands a mystery gift to a mystery person.

**Before takeoff, each traveller gets:**

| | |
|---|---|
| 🎫 **Identity code** | e.g. `QX-417` — yours, keep it secret |
| 🎁 **Target code** | the code you must bring a gift for. You don't know who it is. |
| 👗 **Dress code theme** | the OOTD you must wear to the airport |
| 📦 **Gift brief** | optional silly rule for the gift ("something that makes a noise") |

98 themes across 7 pools: Anime & Cartoon, Fast Food & Brands, Formal & Fancy,
Jobs & Uniforms, Eras & Aesthetics, Airport & Travel Tropes, and Pure Chaos.
Each theme comes with a styling hint so people can improvise with real clothes
instead of renting a costume.

## How a room works

1. One person creates a **room** — names it, sets the headcount (2–20), optionally
   types everyone's names, and picks which theme pools are in play.
2. They hit **Create Room & Roll**.
3. They get **one private link per passenger**, listed by name. Each link is sent to
   that person privately (DM, not the group chat).
4. Opening your link shows your sealed boarding pass — tap to reveal.
5. At the gate: reveal codes, hand over gifts, take photos, lose all dignity.

### The host can't see your pass

The results screen shows only a list of names and copy buttons — **it never renders
anyone's assignment**. Each personal link contains that one person's pass and nothing
else: no other names, codes, or themes are inside it. The only "other person" data in
your link is the target *code* you're gifting, which is exactly what you're meant to
know.

So the person who set up the room can play too, as long as they only open their own link.

> **Being straight about the limits:** this is a static page with no server, so there is
> no way to hide data from someone determined to dig. The host generated the draw, so a
> host who deliberately opens other people's links can see them. What the design
> guarantees is that *passengers* can't peek at each other, and that nobody gets spoiled
> by accident. Organiser tools that do reveal everything (full map, all passes, printing)
> are tucked behind a collapsed, clearly-labelled warning.

### Room memory

**The link *is* the room.** The whole draw is encoded in the URL, and the page rebuilds
it deterministically on every load. So a link:

- never expires and never changes
- shows the exact same result forever
- can be reopened any time before the flight to re-check what you owe your victim
- can't be re-rolled by anyone trying to escape a bad theme

No server, no database, no accounts, no tracking. Just a URL.

### Group-link mode (optional)

If sending 4 DMs is too much faff, the organiser tools also offer one shared group link
where everyone picks their own name from a list. It's more convenient, but the whole
roster travels inside that single URL — so a curious passenger *could* dig it out. Use
personal links if you care about that.

## Fairness

Gift targets are assigned as a **single random cycle**, so everyone gives exactly one
gift and receives exactly one gift, nobody gets themselves, and the chain never splits
into little sub-loops (the classic bug in Secret Santa apps). Verified over 20,000
randomised draws.

## Running it

Open `index.html` in any browser. That's it — one file, zero dependencies, works offline.

## Hosting on GitHub Pages

```bash
git init
git add .
git commit -m "Airport OOTD randomizer"
git branch -M main
git remote add origin https://github.com/<you>/<repo>.git
git push -u origin main
```

Then **Settings → Pages → Source: `main` / root**. Your app will be live at
`https://<you>.github.io/<repo>/` in a minute or two.

Personal links are short. The optional group link gets long with many passengers, since
the whole roster lives in the URL — fine for a group of 4, but if a chat app truncates
it, wrap it with any URL shortener.

## Organiser tools (collapsed by default — they spoil the game)

- **Show all passes** — every pass, sealed until tapped
- **Print passes** — print them to cut up and hand out physically
- **Code → name map** — the full spoiler table
- **Re-roll** — new draw, new links (do this *before* sending anything)
