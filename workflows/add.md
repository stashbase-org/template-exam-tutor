# Add Materials

Materials come in any shape: a textbook chapter, slides, a friend's notes, a past paper, a photo of the whiteboard. They rarely line up with each other. Adding one means reading it and folding what it covers into the topic pages, so each topic has one page with everything I need, whichever file it came from.

## Find what's new

* **Files in library/:** when I say "Add the new materials", look for files in `library/` that aren't listed under Materials in the [index](../notes/index.md).
* **A link:** when there's a file to download, like a PDF, save it to `library/` with `curl -L -o "library/<name>.pdf" <url>`. Otherwise read the page, and list the link itself under Materials.
* **A whole book:** read the chapters that are on the exam, from the scope in [exam.md](../context/exam.md). Tell me which chapters you read and which you skipped.

If you can't read a file, like a blurry photo or a scan with no text, tell me which one, and go on with the rest.

## Read it

Read the whole thing. Note what it covers, how it explains it, and anything particular to my course: a formula written a certain way, a convention like how round robin breaks ties, something the professor said is important. These beat what a textbook says, since they're how the exam is marked.

**Past papers** are read differently. For each question, note its topic, its type (definition, numerical, explain, compare), and its marks. They go into "How it's asked" on each topic page, and show which topics come up most.

**A syllabus** says what's on the exam. Update the scope in exam.md, and tell me what changed.

## Update the topics

1. Decide which topics the material covers. A topic is something you could ask three to five questions on, like "Page replacement", not a whole chapter or unit. When the material has chapters or units, use them as a guide; when it's loose notes, group by idea.
2. Fold the material into each topic's page where it belongs. Don't add a section per source: rewrite the page so it reads as one explanation. Add the material to the page's sources.
3. When something has enough for a page of its own and has none, create one. When a page covers two separate things, split it; when two pages overlap a lot, merge them. Move their entries in [mistakes.md](../mistakes.md) to match, and fix the links.
4. When two materials disagree, go with my course's materials over a textbook, and note the difference under Common traps.

Name the page after the topic, in lowercase with hyphens: `notes/page-replacement.md`.

A topic page looks like this:

```markdown
# <Topic>

<One or two sentences: what it is, and how much it matters on the exam.>

**Sources:** <materials, linked, with the chapter or lecture when known> · <past paper questions>
**My mistakes:** [Mistakes › <Topic>](../mistakes.md#<topic>)

## Key ideas
## How to work it out
## Common traps
## How it's asked
```

* **My mistakes:** only once the topic has entries in mistakes.md.
* **Key ideas:** what I need to know, a line or a few per idea, in my course's terms. Formulas in the form my course writes them.
* **How to work it out:** for topics with numericals, the steps, and one worked example. A past paper question makes a good one. Leave this section out for topics without calculations.
* **Common traps:** where students slip, and where my materials disagree with each other.
* **How it's asked:** from the past papers: which part, what kind of question, how many marks, which years. "No past papers yet" when there are none.

## Update the index

The index looks like this:

```markdown
# <Course>

<One or two sentences: what the notes cover, and what they're built from.>

## What to work on
## Topics
| Topic | In one line | How I'm doing | Last quizzed |
## Materials
| Material | What it is | Topics |
```

* **Materials:** add each new material, with what it is and the topics it feeds.
* **Topics:** add new topics as "Not quizzed yet". How I'm doing is set by quizzes, as in [quiz.md](quiz.md#keep-the-record).
* **What to work on:** two to four items, each a bold title that says it on its own, then a sentence or two with a link. What belongs here: weak topics that come up a lot on the exam, topics I haven't been quizzed on, and parts of the exam my materials don't cover yet. Rewrite the list when things change; don't add to the end.

## Update the dashboard

Last, bring the dashboard's data in line with what you just changed, as in [maintain.md](maintain.md).

## Many materials at once

For setup or a big batch, read everything first. Then settle the topics together, five to ten to start, write the pages, then the index, and the dashboard's data last. Seeing it all at once gives better topics than adding one file at a time. For more than about ten files, or a whole book, tell me how many there are before you start.

## Tell me

In a few sentences: what the material covers, which topics it went into or started, and anything that matters for the exam, like a convention that differs from the book or a part of the exam still not covered. Link the index. Don't list every file you changed.
