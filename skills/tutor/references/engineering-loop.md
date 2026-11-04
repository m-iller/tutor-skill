# Deep Learn: the engineering loop

Use for an engineering concept the user wants to *own*, not just hear about: power electronics topologies, circuits, protocols, data structures, mechanisms, tolerance chains, control loops, embedded peripherals. Method idea credited to devinhuang2001/engineering-learning-skill; written here in our own words and widened beyond embedded code.

**Principle:** understanding ≠ learning. Learned means the user can solve a *new* problem with it.

## Calibrate first
Ask one question: "How familiar are you with X: never heard / know the name / have used it?" (skip if `profile.md` or the message already says).
- New → do every step, extra time on Motivation and Model.
- Know the name → normal pace, weight on Trace and Break.
- Have used it → skim steps 1–2, spend the time on Break, Rebuild and Chain.

## The 8 steps
Deliver one step, then hand the turn back with one short check. Never stack two content steps without a check. Show a one-line tracker at the start of each step, e.g. `X: Motivation ✅ · Model ✅ · Core ⏳ · Trace · Gaps · Break · Rebuild · Chain`.

1. **Motivation, before any definition.** Describe the concrete situation where *lacking* this concept hurts. Example: "A 12 V → 5 V linear regulator at 2 A burns 14 W as heat. That pain is why the buck converter exists."
   Check: "Say the problem in one sentence."

2. **Mental model.** One physical analogy, with each part mapped to a real component, and say where the analogy breaks. (Buck inductor ≈ flywheel keeping current moving while the switch is open; breaks because a flywheel has no saturation.)
   Check: "Which part of the analogy is which component?"

3. **The minimal core.** The smallest working version, annotated with *why* for each line:
   - code → shortest program that works;
   - circuit → simplest schematic + the defining equation(s) with units;
   - mechanism/metrology → simplest sketch or tolerance chain + formula.
   Point out the one "magic" line or relation that makes it work (buck: $V_{out} = D \cdot V_{in}$; ring buffer: `head = (head+1) % N`).
   Check: "Which line/equation is the magic one, and what breaks without it?"

4. **Hand trace.** Give a short scenario to work through on paper: starting state, 5–8 actions, write the state after each. Design it so it hits a boundary (full/empty, discontinuous conduction, max-material condition, overflow, saturation). Then reveal the expected trace.
   Check: "Where did it surprise you?" Notice whether they spotted the boundary themselves.

5. **Feynman gap check, closed book.** Four questions:
   1. What problem does it solve that the simpler approach can't?
   2. What is the key line/relation and why?
   3. How does it behave at the edge cases?
   4. What breaks if you remove part Z?
   Missed 1 → back to step 1; missed 2 → step 3; missed 3 → step 4; missed only 4 → continue, step 6 covers it.

6. **Break it on purpose.** A mutation table: change → predicted failure → what it teaches. Include at least one change that fails *silently* (wrong value, not a crash/explosion) and one that points to the next concept. Have the user predict before revealing.

   | Change | Expected failure | Lesson |
   |---|---|---|
   | Remove the freewheeling diode | Voltage spike kills the switch | Inductor current can't stop instantly |
   | Halve the inductance | Ripple doubles, may enter DCM | What L actually sets |

   For simulations the user can run (LTspice/ngspice, Python, an MCU), let them actually try it.
   Check: "Which failure would be hardest to find in real life?"

7. **Rebuild closed-book, then apply.**
   - A: from a blank page, re-derive / redraw / rewrite the core. What they can't reproduce they don't own yet.
   - B: a transfer problem in a new context (different specs, a real part from a datasheet, a new load).
   Grade with a short coach block: what was right · what needs work · one tip per gap · score /10.
   9–10 → step 8; 7–8 → patch the gaps, then step 8; 5–6 → redo step 3 or 4 on the weak point and re-quiz; ≤4 → restart the loop with a different analogy and example.

8. **Knowledge chain.** Where it leads: a *deeper* version, an *adjacent* concept, and where it appears in real systems, with one line on why each connects. Give 1–3 questions to explore on their own. Add the chain to `progress.md` as upcoming topics.

## By concept type
- **Circuits / power electronics:** motivation = efficiency/heat/size; core = schematic + steady-state equations (volt-second and charge balance); trace = switching intervals; break = remove or resize components, change duty cycle, go into DCM.
- **Mechanisms / machine design:** motivation = what fails without it; core = free-body diagram or kinematic sketch; break = remove a constraint or support, change a dimension.
- **Metrology / tolerances and fits:** motivation = parts that don't assemble or wear out; core = the fit or dimension chain; trace = compute limits at MMC/LMC; break = swap hole-basis/shaft-basis, tighten one tolerance.
- **Protocols / embedded / data structures:** motivation = the wiring or timing problem; core = minimal code + timing diagram; break = remove the boundary check, the mutex, the ACK; include a silent-corruption case.
- **Algorithms:** analogy matters most; trace best, worst and edge cases; break the termination condition or comparison.

## Avoid
- Opening with a textbook definition.
- Showing complex/production versions before the minimal one.
- Skipping the hand trace ("just simulate it").
- Moving on when the user can't state the motivation.
- Listing next topics without saying why they connect.
