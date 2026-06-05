# Writing Audit

> See `__✍️_WRITING_STYLE.md` for full style guide and mirror effect techniques.
> See `__✍️_WRITING_TOOLBOX.md` for optional power techniques (storytelling, open loops, Netflix pacing, etc.).

## Audit checklist (per post)

**1. Does it open with a scene or a thought — not a statement?**
Bad: "Most developers struggle with Rust."
Good: "You're 45 minutes into a compiler error. You've read the message 10 times."

**2. Is there a hyper-specific internal monologue?**
Not what the reader *does* — what they *think* at 11pm when no one's watching.
Look for vague phrases like "you felt frustrated" or "you were stuck" — replace with the exact thought.

**3. Is there a secret named that they've never said out loud?**
The most powerful line in the post is usually the one they've had in their head but never admitted.
If it's not there, add it.

**4. Is the language raw enough?**
Read it aloud. Does it sound like a human who lived it, or a manual?
"shit, the compiler is angry again" > "you may encounter compiler errors"

**4b. Every sentence needs a verb.**
Noun fragments and gerund lists are not sentences. They sound like AI bullet points dressed as prose.
Bad: "Something specific to build. Someone reviewing their code. A reason to stay."
Bad: "Nodding. Saying nothing." / "Skilled. Knowledgeable. Paid well."
Good: Make it a real sentence with a subject and verb. "They had a project waiting for them, someone reading their code, a reason that existed outside their own willpower."
Short punchy sentences are fine — as long as they have a verb. "That's fixable." ✓ "Nodding." ✗

**4c. Never use "Not because X", "Not: X", or any negation-first contrast — even once.**
It's everywhere on LinkedIn. It signals AI-written content immediately.
Bad: "Not because your portfolio is weak. Not because the market is slow."
Bad: "Not: which language is most elegant. Not: which has the best community."
Also bad: "Not because it was trendy. Because correctness at that scale isn't optional."
Good: Just say the real thing directly. Cut the negation entirely.
"The ratio. That's it. Everything else was noise." — not a single "not".
Bad: "Skilled. Knowledgeable. Paid well." — sounds like AI generating bullet points as prose.
Good: Write it as a real sentence. "They knew every route, every airline quirk, every trick to get you a good seat."
If you're using short sentences for rhythm, make sure each one is a complete thought — not a label.

**4d. Never use em dashes (—).** Replace with a period, comma, or colon. It's the most reliable AI-writing signal on LinkedIn.

**5. Are there robotic lists that could be prose?**
See style guide. Not all lists are bad — but check if they kill the rhythm.

**6. Does the ending land?**
Last line before the CTA should hit. Not summarize — hit.

**7. Is the CTA correct for the funnel stage?**
- TOFU → `Follow me.` (make peope understand they have an issue)
- MOFU → `My DMs are open.` (issue + solution)
- BOFU → `If this is you — my DMs are open.` (issue + solution to someone already tried)

---

## Audit process

1. Read all titles first — spot thin ones (no scene, no tension)
2. Work in batches of 5
3. For each post: run the 6 checks above
4. Note what's missing, rewrite, update in DB
5. Move to next batch
