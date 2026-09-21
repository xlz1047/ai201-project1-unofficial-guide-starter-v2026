# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
Most `campus_life` documents are short posts where the useful fact is usually
in one sentence, so I expect retrieval to work for most questions. I left one
question as room for an unusually weak match or a topic with less coverage.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
The pipeline keeps each retrieved chunk's source filename with the context
given to generation, so naming a source should be achievable for every answer.
I chose all five because an answer without a source is not useful for checking
short factual posts.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

<!-- The five questions are the ones in `OUT_OF_SCOPE` at the bottom of
     `questions.py`, and `run_eval.py` puts them through the gate and writes
     what happened into your run log. Swap them for your own if you'd rather —
     just keep five of them, or the "4 of 5" above has nothing to be 4 of. -->

**Why this target:**
The five out-of-scope questions are from unrelated domains, while this corpus
is narrowly about university life. A target of 4 of 5 allows for one accidental
semantic match while still requiring the gate to reject nearly all unrelated
questions.

---

## 4. Something about your chunks

At least 4 of 5 sampled chunks should read as a complete thought, with no
sentence cut in half at either end.



**Why this target:**
The documents I read are short posts with one or two paragraphs, so a useful
chunk should normally contain a whole fact rather than a fragment. Four of five
allows for one boundary case while still checking that chunking fits this
corpus.



---

## 5. Your choice

For at least 4 of 5 in-corpus questions, the answer should name the source
document that contains the fact used in the answer, not just an unrelated
retrieved document.



**Why this target:**
Source accuracy matters because several posts cover similar university topics,
and a filename is only useful if it points to the evidence. Four of five keeps
the target demanding while allowing one possible attribution mistake.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
