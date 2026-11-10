# Exam Tutor

An exam is coming, and you have a pile of stuff to study from: the textbook, slides, your class notes, a friend's notes, a couple of past papers. Rereading it all feels like studying, but it doesn't stick. Testing yourself works much better. But someone has to write good questions, check your answers, and show you where you went wrong.

This project makes AI your tutor. Drop in whatever you have; messy is fine. It reads it all and writes study notes, one page per topic, with the formulas the way your course writes them, and how each topic shows up in past papers. Then it quizzes you, one question at a time, in your exam's style. You answer, and it marks your answer and explains where you went off. Everything you get wrong goes into a mistake log, and comes back later as a new question until you get it right.

## Getting started

Open this project in StashBase and tell the Agent:

1. **"Set me up."** It asks two things: what you're studying for and when the exam is, and what you have to study from. Drop your files into `library/` before you start or when it asks. Past papers help most: it learns from them how your exam asks. Then it writes your study notes and asks you the first question.
2. **"Quiz me."** Answer in Chat. It marks your answer, explains, and asks the next one. It starts with what you got wrong before, then your weakest topics. Or say "Quiz me on paging" or "Quiz me on my mistakes."
3. **"Add the new materials."** Got new slides, or another past paper? Drop them into `library/` and say this. It folds them into your notes.

Open the dashboard, `index.html`, to see where you stand at a glance. It shows what to say in Chat, too.

You can also:

* **Ask anything.** For example, "Explain the TLB like I've never heard of it," or "Why does wait(empty) come before wait(mutex)?"
* **Say "Give me a mock exam."** It sets a paper in your exam's format, asks the questions one by one, and marks them all at the end.

Before the exam, read `mistakes.md`. It's every question you got wrong, with the right answer and why.

One project is one course. Studying for several exams? Make a copy for each.

The template comes with an example: a third-year computer science student getting ready for an Operating Systems end-semester exam. Their materials are messy class notes, a friend's notes on deadlocks, a list of doubts, two past papers, and chapters of [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/), a free textbook. From these come five topics, from CPU scheduling to page replacement, and a week of quizzes so far: six mistakes, two of them fixed. Browse it, or say "Quiz me" to try it, before running setup. Setup replaces it with yours. The book's chapters aren't included; the notes link to them online.

## The dashboard

The notes and the mistake log are all text, and you never have to open anything else. The dashboard sits on top of them, and the Agent keeps it current after every quiz.

* **Topics:** how you're doing on each, what's left to retry, and when it was last quizzed. Each topic opens its notes.
* **Mistakes:** what's still to retry, and what you've fixed.
* **Practice:** how many questions you've answered so far, as a line that keeps climbing, and how many each day.
* **Focusing on:** the topics that need you most right now.

## Requirements

An Agent that can run local commands, to download files from links. No API key is needed.

## Make it yours

Setup covers most of it. You can also change things anytime:

* **Who you are, and how you like things explained,** are in `context/profile.md`.
* **Your exam: its date, format, and what's on it,** is in `context/exam.md`.
* **How study notes are written** is in `workflows/add.md`.
* **How quizzes work:** what gets asked, how answers are marked, and how mistakes are kept, is in `workflows/quiz.md`.
* **What the dashboard shows,** and how the Agent keeps it current, is in `workflows/maintain.md`.
* **The tutor's persona and rules** are in `AGENTS.md`.

## Files

* `AGENTS.md`: the tutor's persona, the rules for getting things right, and the task index.
* `CLAUDE.md`: points Claude Code to `AGENTS.md`.
* `context/profile.md`: who you are, and how to explain things to you.
* `context/exam.md`: your exam's date, format, and what's on it.
* `workflows/setup.md`: the setup Q&A.
* `workflows/add.md`: how materials become study notes, with the page formats.
* `workflows/quiz.md`: quizzes, mock exams, explanations, and how mistakes and progress are kept.
* `workflows/maintain.md`: how the Agent keeps the dashboard in line with the notes, and the format of its data.
* `library/`: your materials. The Agent reads them and never changes them.
* `notes/index.md`: the map: what to work on, every topic and how you're doing on it, and every material.
* `notes/`: one page per topic.
* `mistakes.md`: every question you got wrong, the right answer, and whether you've fixed it.
* `index.html`: the dashboard.
* `assets/study.json`: everything the dashboard shows, including how many questions you answered each day.
* `assets/banner.svg`: the dashboard's banner.
