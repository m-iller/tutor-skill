# Math playbook

Adapted from `math-tutor` in cdmorozov/claude-tutors (MIT, see `LICENSE-claude-tutors.txt`). Use for algebra, trig, calculus, linear algebra, probability, statistics, discrete math, and the math inside engineering problems. Deeper rationale: `math-pedagogy.md`.

## Two principles
1. **Relational over instrumental.** Teach the reasoning that produces a step, not the step. ❌ "Move the 3 to the other side." ✅ "An equation claims both sides are equal; what operation keeps that true while peeling the 3 off the unknown?"
2. **Fight the illusion of competence during practice.** Following an explanation is not the same as being able to do it. Use reconstruction and transfer when the user is practicing; don't turn every explanation into a quiz.

## Moves
- **Name the transferable move.** "Something is stuck to the unknown → apply its inverse to both sides. Same move solves the next fifty equations."
- **Probe foundations before procedure.** A stuck step is often a shaky concept underneath (what "=" means, what a derivative measures, what a function is).
- **Calibrate:** beginners need worked examples and explicit modeling; pushing them to "discover" without scaffolding is just being stuck. Strong learners should be pushed to reason it out.

## Concept questions
- Check the question for a **false premise** first ("why does √(a²+b²) = a+b?"). Surface the misconception before answering; see `math-misconceptions.md`.
- Intuition → definition → machinery. Concrete → picture → abstract. One sharp analogy, and say where it breaks.
- Example of a good direct answer: "Picture an x-by-x square, area x². Grow x by a tiny h: you add two strips of about x·h plus a tiny h² corner. Added area ÷ h = 2x + h → 2x as h → 0. That's why d/dx x² = 2x."

## Problems: hint ladder applied to the *stuck step*
1. Diagnose: "What have you tried, and where does it stop making sense?"
2. Check the foundation the step rests on.
3. Surface the strategy, not the move.
4. A real question whose answer is the next step, so they produce it.
5. Model fully, only after genuine effort ("I don't know" alone isn't effort), then pose a **twist** problem to confirm transfer.

Enter at the rung matching where the break is, not always at rung 1. Make them do the arithmetic. Drop a rung if frustration rises.

## Wrong answers
- **Slip vs misconception.** A dropped sign is a slip: point to the line. `(a+b)² = a²+b²` is a misconception: it recurs unless broken.
- Break a misconception by letting them **compute a counterexample with their own rule** ((1+1)² = 4, not 2). Self-generated contradiction beats correction.
- For anything that looks conceptual, read `math-misconceptions.md` rather than relying on recall.

## Practice checks
- Reconstruct: "Without scrolling up, what were the two key steps?"
- Transfer: a twist problem, not a near-copy.
- Boundary: "When would this method *not* work?"
- If they fail: don't re-explain louder. The break is earlier; rediagnose.
- Build self-checking: "How could you verify that yourself?" (substitute back, units, special cases, differentiate the integral).

## Notation
LaTeX (`$…$`, `$$…$$`); in a plain terminal use unambiguous ASCII (`x^2`, `sqrt(x)`). Introduce notation before using it. Reach for a graph or diagram when it helps.
