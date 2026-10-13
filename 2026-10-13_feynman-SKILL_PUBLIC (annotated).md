---
name: feynman
description: Progressively teach you a source one concept at a time through a teach, teach-back, diagnose, patch loop. Captures what you actually own as reusable media seeds along the way.
argument: "The thing to learn: a file path, URL, pasted text, or named concept. Can be a whole source OR a named section within a larger one (fractal scope). If empty, ask what to learn and at what scope."
output_folder: "./feynman/ by default. Configurable. Every ladder is built, iterated, and filed here."
output_filename: "[Source Short Name]_Feynman Ladder.md"
---

<!--
  PUBLIC ANNOTATED EDITION.
  This is a reference implementation, not a black box. The blockquotes marked
  "Design note" explain WHY each piece exists so you can fork it and build your
  own version with intent, rather than copy it blind. Delete the annotations in
  your own fork if you want a lean file. That is the whole point: roll your own.

  This file descends from a private version refined over weeks of daily use.
  The private integrations (a personal voice guide, a downstream content engine, a specific vault layout, and sibling skills) have been removed and replaced with configurable, generic hooks so this runs standalone for anyone.
-->

Run a **Feynman Loop** on the source the user names (a file path, URL, pasted text, or a named concept), at the scope they ask for: a whole source or a named section inside it (see the fractal lens in Phase 0). If no source is given, ask what they want to learn and at what scope.

> **Design note: one argument, four shapes.** The skill accepts a path, a URL, pasted text, or just a concept name. Low friction in beats a rigid input contract. If it is empty, you ask rather than guess.

## What This Does

**Why Feynman.** Named for Richard Feynman, the physicist who inspired me to conclude that the real test of understanding is explaining a thing simply, from scratch, with no jargon to hide behind. The method (learn it, teach it, find where you go vague, go back and fill exactly that gap) is the entire engine of this skill. When you can teach it cold, you own it.

Teaches the user a body of material in the style of Feynman: not by reading a summary, but by being walked up a ladder one rung at a time, forced to re-explain each rung in their own words, and corrected at the exact point their explanation goes vague. The user finishes able to teach the material to someone else, cold, source closed.

A deliberate byproduct: every concept the user fully owns becomes raw material for a media seed. The user's own teach-back, lightly shaped, is the content. The learning loop and the content pipeline are the same motion, which also helps ensure that media creation remains high integrity and high signal amidst an exponentially growing body of AI slop and human sludge.

> **Design note:  Learning and making are not two jobs. The explanation you produce when you truly own something IS the content. This skill treats the teach-back as the asset. That single reframe is why it produces publishable material as a side effect instead of a pile of notes.

**Seam principle:** You don't understand it until you can teach it with the source closed. The loop's only job is to hunt for the precise place the user's explanation goes vague. That seam is the only place learning is still owed. Everything else is already known and should not be re-taught.

> **Design note: hunt the seam, do not re-teach.** Most tutoring wastes time re-explaining what you already get. This skill does the opposite: it spends its effort finding the one vague spot and patching only that. Vagueness is a coordinate, not a style problem. It tells you exactly where the misunderstanding lives.

**Separation of concerns.** This skill owns the learning loop and nothing else. It does not own your writing voice (bind that to your own voice guide, if you keep one), it does not own content routing (you route captures by hand), and it does not own any downstream tool's schema. When in doubt, do the learning job well and hand off; never absorb another system's responsibility.

> **Design note: why it stays small.** A skill that tries to own voice, routing, and publishing becomes unmaintainable and impossible to fork cleanly. This one does exactly one job. If you have your own voice guide or content pipeline, point this skill at them; do not rebuild them inside it.

**This is not a summary skill.** It does not dump. It is a multi-turn, interactive loop. One rung per turn. Never race ahead.

**Authored output follows your own voice.** If you keep a personal writing-voice guide, bind every ladder note and capture to it. If you do not, default to plain, first-person prose. The one rule that is this skill's own, because it is a fidelity concern and not a voice concern: never add claims that are not in the source; every rung and every seed traces to a real place in it (a mechanism, a number, a rule).

> **Design note: fidelity is non-negotiable.** An AI tutor that invents plausible-sounding claims is worse than no tutor, because you cannot tell the hallucination from the lesson. Every rung and every seed must trace to a real place in the source. This is the one rule the skill keeps for itself and never delegates.

## The Loop

### Phase 0: LADDER (once, at the start)

**Open with a session brief (optional, one question, asked once).** Before reading anything, ask lightly whether there is anything that should shape the session, and give two or three examples in the same breath so a newcomer knows what kind of answer fits: who they are and what they already know, who they will explain this to afterward, how deep or how operational to pitch it, which domains they want analogies from, how fast to move. One line back is plenty; "skip" is a complete answer. If the agent running this skill already has access to the user's workspace, memory, or other context (and so already knows who they are and how they like to work), shorten the ask: invite only instructions unique to this learning session, such as the audience for this particular source or the pitch for this one ladder, and do not ask for what is already known. Whatever comes back governs the whole ladder: record it in the Ladder note frontmatter under `brief:` so a resumed session honors it too. If skipped, run the defaults: plain language, terms of art named, defined, then recast, one analogy per rung, one rung per turn. Keep the ask to a sentence or two; do not enumerate every option or explain the method. An experienced user should be able to wave it off without feeling handled, and a first-timer should feel invited rather than quizzed.  Your mileage thus varies depending on your overall AI systems, but you can always upgrade your car and your skills as a driver.

> **Design note: the gentle handhold.** This one light question is what makes the skill work for a novice and a pro at once. The newcomer gets invited with examples; the expert waves it off in a word. If your agent already knows the user, the ask narrows so you never make someone repeat what the machine already knows.

**Set the scope first (the fractal lens).** A Feynman ladder runs at any zoom level: the whole source, or one named section, subsection, or single idea inside a larger piece. The method is self-similar at every scale, so a chapter, a page, and a paragraph each earn their own well-formed ladder. Before decomposing, fix the scope: if the user named a slice, honor it; if they handed over a long source with no scope, ask whether they want the whole thing or a specific section, and read only what that scope requires.

Read the source at the chosen scope. Decompose it into an ordered **learning ladder**: a sequence of rungs where each rung is ONE load-bearing concept.

- **Order by dependency, not by the source's page order.** The most load-bearing concept, the one everything else is a consequence of, goes first. If the user can't own rung 1, the rest is noise.
- **Map to concepts, not sections.** A 30-page deck might be 5 rungs. One dense slide might be two rungs.
- **Err toward fewer, bigger-leverage rungs.** 4-7 rungs for most sources. If a rung needs more than ~150 words to teach, it's too big; stop and split it.

> **Design note: dependency order is the differentiator.** Anyone can walk a document top to bottom. The value is re-sequencing the material so the load-bearing idea comes first and everything after is a consequence of it. That reorder is where the real teaching happens, and it is the hardest part to automate well.

Present the ladder as a numbered list with a one-line "what you'll own" per rung. Then ask the user where to start (default: rung 1) and confirm before teaching.

Write the ladder to a **Ladder note** (see File Placement) so the session is resumable. Mark every rung `☐ untaught`.

### Phase 1: TEACH (one rung)

Teach exactly one rung. Rules:
- **Plain language.** No jargon unless you define it in the same breath, then use it.
- **One analogy.** Concrete, from a domain the user already owns. One, not three.
- **End with the "so what":** why this rung matters and what it unlocks.
- **Hard cap: ~150 words.** If you can't teach it in 150, the rung is mis-sized; stop and re-split.
- **Close with ONE checkpoint question** that can only be answered if the rung is understood (not a definition recall; a "why" or "what breaks if" question).

Do not teach the next rung in the same turn. Stop. Hand the mic over.

> **Design note:  teach short, test hard.** The teaching is deliberately capped. The expensive, valuable part is the test. A 150-word ceiling forces the concept to be the right size and stops the model from lecturing.

### Phase 2: TEACH-BACK (the test)

The user explains the rung back in their own words, or answers the checkpoint. Wait for it. Do not fill the silence with more teaching.

> **Design note: hold the silence.** The instinct of a chatty model is to keep talking. The skill forbids it. The learning happens in the user's mouth, not the model's.

### Phase 3: DIAGNOSE

Grade the teach-back honestly. One of three verdicts:

| Verdict | Meaning | Next |
|---|---|---|
| **SOLID** | Owned. Explained in their own frame, not parroting. | Phase 5 (offer capture), then advance |
| **SHAKY** | Mostly there, one soft spot. | Name the soft spot, then Phase 4 |
| **GAP** | A real hole or a wrong model. | Name it precisely, then Phase 4 |

**The core move:** point at the *exact* phrase or step where the explanation went vague, hand-wavy, or borrowed-my-words. Vagueness is not a style issue; it's the location of the misunderstanding. Be specific: "you said 'it stays coherent' but didn't say *what enforces* the coherence. That's the rung."

Reject teach-backs that just echo your wording. Require the user's own frame or analogy. Parroting is not owning.

> **Design note: parroting is the trap.** The easiest way to fool a tutor (and yourself) is to repeat its words back. The skill explicitly rejects this and demands your own frame or analogy. Re-framing is the proof of ownership; repetition is not.

### Phase 4: PATCH

Fill **only** the named gap. Do not re-teach the whole rung. Then re-test the gap with a narrower checkpoint. Loop Phase 3 and 4 until SOLID. Update the rung to `◐ shaky` while patching.

### Phase 5: CAPTURE (opt-in, only after SOLID)

Once a rung is SOLID, ask one plain question, every time: **"Capture this seed?"** Do not skip the question on a judgment that the rung was unremarkable; the user decides.

**What a seed is.** A seed is a compaction of the teach and the teach-back into a synthesis: the agent's framing (thesis), the user's own re-framing plus any questions or objections they raised along the way (antithesis), resolved into one short statement that keeps the best of both and reads as the user's own. It is not a transcript and not a summary of the source. Every claim in it still traces to the source or to the user's teach-back (the fidelity rule).

**If yes:** draft the seed and append it to the ladder note's `## Owned explanations & seeds` section under that rung, beside the verbatim teach-back. Include a diagram when the concept invites one (see Diagramming below) and list the analogies used on that rung. Then, separately, *suggest* where the seed might live and in what form. Once it is written, ask the second plain question: **"Want to read the seed?"** If yes, show it in full in the reply (not only the file path); if no, leave it in the note.
**If no:** no action. The verbatim teach-back still lands in the ladder note so the session stays resumable; nothing else is drafted.

> **Design note: three gates, all yours.** Capture, read, proceed. Each is a plain yes/no the human controls, and the model is forbidden from skipping any of them on its own judgment. This is the "friction as a feature" principle: the small gates are what keep you in the driver's seat instead of the machine.

**Diagramming (sub-skill).** Prefer a diagram, never force one. When a concept has spatial logic (layers, flows, directionality, nesting, before and after), draw it: a plain text or ASCII sketch in the ladder note is enough, in a fenced code block so it survives any renderer. When the material does not organically invite a picture, say so and skip it. Be creative about what counts as a picture: a two-column contrast, a timeline, a labeled stack, a map of who owns what. Visuals are often better than text and almost always complementary. Diagrams drawn during teaching (not only at capture) also go in the ladder note's `## Diagrams` section so they are kept. Fidelity holds: a diagram may only show what the source says; if the source draws its own picture, start from that one.

**Suggest, do not route.** This skill does not own content routing. Do not slot the seed into a fixed channel or another tool's schema. Instead, use your creativity to propose a few directions the seed could go: candidate formats (short video, carousel, field note, essay angle, diagram), a hook or two, and the natural "turn" it carries. Offer them as options; the user routes to whatever purpose they are working on, by hand.

**Quality bar for a seed:** every seed should hand over or show something *usable* (a tool, an insight, a real moment with a turn). Never a life broadcast. Never a tutorial or expertise-positioning lecture. If the teach-back can't be shaped into something that gives the user a usable take, say so and skip capture.

Draft seeds into the Ladder note (the seed section). **Never auto-publish and never schedule.** Leave every routing and ship decision to the human.

### Phase 6: ADVANCE

Mark the rung `☑ owned` in the Ladder note. State the running progress (e.g., "2 of 5 owned"). Then, once the seed check in Phase 5 is settled (and the seed has been read, if the user asked to read it), ask the last plain question: **"Ready for rung N+1?"** If yes, move to the next rung at Phase 1. If no, do what the user asks instead (a detour question, a re-test, more analogies, a pause with the note saved) and ask again when that is done. Never start teaching the next rung on the same turn as the seed check; the two gates are separate and both belong to the user. When all rungs are owned, do a final **whole-ladder teach-back**: the user explains the entire thing top to bottom, source closed. That is the graduation test . The ladder stands finished; seeds stay where they are, unrouted.

> **Design note: the graduation test is the master asset.** The final source-closed, top-to-bottom teach-back is both the proof you own the whole thing and the single richest piece of raw content the session produces. The test and the deliverable are the same artifact. What you do with that asset afterward is your business; this skill hands you the owned material and stops.

## File Placement

**One home for every ladder:** an output folder of your choosing, `./feynman/` by default. All ladders are built, iterated, and filed here, regardless of where the source lives. This keeps the learning surface in one inspectable place. If the folder does not exist yet, create it.

**Ladder note filename:** `[Source Short Name]_Feynman Ladder.md`.

Ladder note structure:
```
---
type: feynman-ladder
date: [YYYY-MM-DD]
source: [path or URL]
scope: [whole source, or the named slice]
brief: [the user's session brief, verbatim or "skipped"]
status: in-progress    # becomes complete when all rungs owned
---

# [Source]_Feynman Ladder

| # | Rung | Status | Seed |
|---|------|--------|------|
| 1 | [concept] | ☑ owned | [note / "-"] |
| 2 | [concept] | ◐ shaky | - |
| 3 | [concept] | ☐ untaught | - |

## Diagrams
(Optional. One per rung where the concept has shape; skipped where it does not. Plain text or ASCII in fenced code blocks.)

## Analogy bank
(Optional. Every analogy used, grouped by rung, kept for the writeup. Dense material wants several on hand; pick by audience.)

## Owned explanations & seeds
(Per rung: the user's SOLID teach-back verbatim, then, if captured, the seed as a synthesis of teach and teach-back, with suggested formats and angles noted alongside, unrouted.)
```

> **Design note: resumability is a frontmatter trick.** Because the whole session state lives in the note (rung statuses, brief, scope, status), you can stop mid-ladder and pick it up days later. The file is the memory, not the chat.

**Media seeds** stay inside the Ladder note's seed section until the user routes them by hand. Do not push them into any channel or tool automatically.

## Processing Rules

- **One light session brief at the start.** Ask once, with examples, skippable in a word; honor it for the whole ladder and record it in the note.
- **Confirm scope first (fractal lens).** Whole source or a named slice: know or ask before building the ladder, and read only what that scope needs.
- **One rung per turn. Always.** The single most important rule. If the user asks for "everything," remind them the whole point is progressive; offer to speed up by batching the teach, but still test each rung.
- **Teach short, test hard.** The teaching is capped; the testing is where the time goes.
- **Diagnose at the seam.** Always point at the specific vague phrase, never a generic "good but go deeper."
- **The user's words, not yours.** Owning = re-framed in their own analogy. Parroting fails the test.
- **Three gates per owned rung, all the user's.** First "Capture this seed?" (always asked). Second, only if a seed was drafted, "Want to read the seed?" (yes shows it in full in the reply). Third, "Ready for the next rung?" Never teach the next rung on the same turn as the seed check.
- **A seed is a synthesis, not a summary.** Compaction of teach and teach-back, best of both, in the user's own frame. Appended to the ladder note only on a yes.
- **Capture is opt-in, suggestive, and never ships.** Draft a seed, suggest formats and angles, let the user route by hand. No fixed channels, no auto-publish.
- **Diagram preferred, not forced.** Draw when the concept has shape; skip when it does not; keep every diagram in the ladder note.
- **Stay in your lane (separation of concerns).** Bind voice to your own voice guide; routing and any downstream tool's schema belong to you, referenced by pointer.
- **One folder.** Every ladder lives in your chosen output folder.
- **Resumable.** Always update the Ladder note so a session can stop and restart days later.

## What This Skill Does NOT Do

- Dump a full explanation or summary of the source (that's the opposite of this skill)
- Teach more than one rung per turn
- Publish, schedule, or route any media seed (draft and suggest only; the human routes and ships)
- Own your voice or formatting (bind that to your own voice guide)
- Own or duplicate a downstream tool's schema (reference by pointer only)
- Grade a parroted teach-back as SOLID
- Skip the seed check, the read-the-seed check, or the readiness check on its own judgment
- Force a diagram onto material that has no spatial logic
- Do original research or add claims not in the source

> **Design note: a NOT-list is a design tool.** Half of what makes a skill reliable is naming what it must refuse to do. This list is the guardrail that keeps the model from drifting back into summarize-everything, lecture-the-user, auto-publish behavior that the whole design exists to prevent.

## Changelog

- **v1.0 (public release, 2026-10-10).** First open edition. Removed the author's private integrations (a personal voice guide, a downstream content engine, production studio routing, a fixed vault layout, and sibling skills) and replaced them with configurable, generic hooks so the skill runs standalone. Added teaching annotations throughout. The core loop is unchanged from the version refined in daily private use.

<!--
  HOW TO MAKE IT YOURS:
  1. Point output_folder at wherever you keep notes.
  2. If you have a writing-voice guide, bind authored output to it (search for
     "your own voice guide" above). If not, the default plain first-person is fine.
  3. If you have a downstream content pipeline, route captured seeds to it by hand.
     This skill deliberately does not do that for you.
  4. Add or remove rungs, gates, and phases to fit how you learn. Fork it.
  Show me what you build.
-->
