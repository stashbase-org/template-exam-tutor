# Quiz

Answering questions teaches me more than rereading, and my mistakes show what to fix. A quiz goes one question at a time: you ask, I answer, you mark it and explain. Everything I get wrong goes into [mistakes.md](../mistakes.md) and comes back later as a new question, until I get it right.

## Pick the questions

What I say decides where questions come from:

* **"Quiz me":** a mix. An open mistake or two first, then my weakest topics, then topics I haven't been quizzed on in a while. Favor what comes up most in past papers, and stay within the exam scope.
* **"Quiz me on <topic>":** only that topic, easy to exam-level, starting with its open mistakes.
* **"Quiz me on my mistakes":** only open mistakes.

An open mistake comes back as a new question on the same point, with new numbers or a new angle. Not the same question again: I'd just remember the answer.

A quiz is about five questions unless I say otherwise. I can stop anytime.

## Ask

* One question at a time. Then wait for my answer.
* Ask the way my exam does, from exam.md and the past papers: definitions, numericals, compare-and-contrast, explain-with-a-diagram. Mix them. When neither says how my exam asks, mix definitions, short explanations, and numericals where the topic has them. Start each question with its topic and marks, like "(Paging, 4 marks)", so I know how much to write.
* Make up your own numbers for numericals. Use a past paper question as is only when I ask for past papers.
* Solve the question fully before you ask it, as in [Getting it right](../AGENTS.md#getting-it-right).

## Mark and explain

Start with the verdict: right, partly right, or wrong. For partly right, say which part is right. "I don't know" counts as wrong; go straight to the explanation.

Then explain, starting from where I went off, not from the beginning:

* **For a numerical,** go through my steps and find the first one that's wrong. Show the right working from there, laid out the way I'd write it in the exam, with the Gantt chart or table if it has one. If I gave only a final number and it's wrong, ask for my working first, unless the number alone shows the slip.
* **For a written answer,** say what's missing or off, then what a full-marks answer has, in a few lines. Marks come from points, not length.
* Keep it to what I need to get it right next time. Use my course's terms and notation, and name the topic page and the source, like "OSTEP ch. 19" or "lecture 8 notes".
* If my answer's right, say so in a line. Add one thing only if it's worth knowing for the exam, like how this question usually gets twisted.

If I ask a follow-up, answer it before the next question. If a question you asked turns out to be wrong or unclear, say so, and leave it out of the record.

## Keep the record

After each question, before the next one:

* **Wrong or partly right:** add it to mistakes.md under its topic, in the format below.
* **A retry I got right:** mark that mistake fixed.
* **A retry I got wrong again:** keep it open, and add the date.

When the quiz ends, or I stop:

* Update "How I'm doing" and "Last quizzed" for each topic in the [index](../notes/index.md), and rewrite "What to work on", as in [add.md](add.md#update-the-index).
* If I slipped on something most students slip on too, and the topic page doesn't mention it, add it to the page's Common traps.
* Bring the dashboard's data in line: today's questions, the mistakes, how I'm doing, and the topics to focus on, as in [maintain.md](maintain.md).
* Tell me in a few sentences: how many I got right, what I keep missing, and what's improved. No pep talk.

How I'm doing on a topic, judged from the last few quizzes on it, not just today:

* **Shaky:** I miss more than I get, or I have open mistakes on the main calculations.
* **Getting there:** mostly right, with an open mistake or two, or right so far only on the easier questions.
* **Solid:** right across a couple of quizzes, including exam-level questions, with no open mistakes.
* **Not quizzed yet.**

A mistake looks like this:

```markdown
### <The point I missed, as a lesson, like "Banker's algorithm: compare Need, not Max, with Available">

**Status:** To retry · missed Nov 5
<or: Fixed Nov 8 · missed Nov 5>

**Question:** <the question as you asked it, with its topic and marks>

**My answer:** <what I said, short; for a numerical, the step that went wrong>

**Right answer:** <the answer and the working, short>

**Covered in:** [<Topic>](notes/<topic>.md), <the source>
```

Name each mistake after the point I missed, so the file reads like a list of lessons.

## Mock exam

When I ask for a mock exam, set a paper in my exam's format from exam.md: the same parts, number of questions, and marks, across the whole scope, weighted like the past papers. Ask the questions one at a time, as in a quiz, but don't mark or explain anything until I've answered them all. Then give the marks for each question and the total, and explain the ones I lost marks on. Keep the record as above.

A smaller mock is fine too, like "Mock Part A" or "One Part B question."

## Explain

When I ask about something outside a quiz, like "Explain the TLB" or "Why does wait(empty) come first?":

1. Start from the topic page. When it's not detailed enough, go back to my materials in `library/`.
2. Explain it the way profile.md says I learn best. Keep it short; I'll ask for more.
3. Say where it's from. If my materials don't cover it, say so.
4. If your explanation is clearer than the topic page, or fills a gap in it, update the page.
