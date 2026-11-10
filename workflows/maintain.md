# Keep the Dashboard Current

The dashboard is `index.html`: how I'm doing on every topic, my mistakes, how many questions I answer each day, and the topics I'm focusing on. Every topic opens its page, and every mistake opens mistakes.md. The page can't read the notes, so what it shows comes from `assets/study.json`, and keeping that file in line with the notes is your job. The index and mistakes.md stay the source; the one thing only the JSON keeps is how many questions I answer each day. StashBase shows the change within a couple of seconds, even while the dashboard is open.

## When to update it

* **After a quiz or mock exam:** add today's questions to `answered`, and update `topics`, `mistakes`, and `focus`. This is the last step of keeping the record in [quiz.md](quiz.md#keep-the-record).
* **After adding materials:** new, renamed, merged, or split topics, and `focus`. This is the last step of [add.md](add.md).
* **At setup:** replace the example with my course: set `course`, empty `topics`, `mistakes`, `answered`, and `focus`, then fill them from the new notes. Leave out `example`.

## Editing rules

* Keep it valid JSON. Change only what you need, and leave every other field as it is, including fields not listed here.
* A topic's `id` is its page name, like `page-replacement`. The dashboard links to `notes/<id>.md`, so the ids must match the files. When a topic is renamed, merged, or split, update its id everywhere it appears.
* Dates are `YYYY-MM-DD`.
* Don't change `schemaVersion` or `index.html`.

## Format

```json
{
  "example": true,
  "course": "Operating Systems",
  "focus": ["paging", "cpu-scheduling"],
  "topics": [{ "id": "paging", "name": "Paging and the TLB", "level": "shaky", "lastQuizzed": "2026-11-09" }],
  "mistakes": [{ "title": "EAT: a TLB miss still pays for the TLB lookup", "topic": "paging", "missed": ["2026-11-06"], "fixed": "2026-11-12" }],
  "answered": [{ "date": "2026-11-09", "questions": 6 }]
}
```

* `example` is `true` only while the template's example is in place; the dashboard then also tells people to say "Set me up." Setup removes it.
* `course` is the index's title.
* `focus` lists the topics named in "What to work on" in the index, by id, most important first. Items that aren't a topic, like a part of the exam my materials don't cover, stay in the index only.
* `topics` follow the index's Topics table, in the same order. `level` is `shaky`, `getting-there`, `solid`, or `new` (not quizzed yet), from "How I'm doing". `lastQuizzed` is its "Last quizzed"; leave it out until the topic has been quizzed. The dashboard counts what's left to retry from `mistakes`, so don't store it.
* `mistakes` follow mistakes.md, in the same order. `title` is the mistake's heading. `missed` lists every date I missed it. `fixed` is the date I got a retry right; leave it out while the mistake is open.
* `answered` has one entry per day I answered questions, oldest first: the `date`, and how many `questions` I answered that day, right or wrong. After a second quiz on the same day, add to that day's number.

## Size

The data holds up to 500 KB and 20,000 values. A semester of mistakes and daily counts fits easily. If it gets close, tell me, and offer to drop fixed mistakes from more than a month ago; they stay in mistakes.md.
