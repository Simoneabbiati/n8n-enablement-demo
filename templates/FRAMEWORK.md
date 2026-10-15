# GTM Academy — course framework (for writing GTM101–GTM112)

Use this to write each course as JSON. The site renders it with templates/course.template.html.
A complete reference example is templates/course-example.GTM101.json. Follow its shape exactly.

## 1. Inputs per course
Take these from templates/academy-data.json (the `courses` array): id, title, path, level/levelId, roles, competencies, moments, prereq, scenario, assessment, minutes.
Take goals and pain points per role from the `roles` array. Never invent new roles, levels or competencies.

## 2. Structure — every course has these 9 sections, in this order
1. **who_its_for** — 1–2 sentences: role, level, moment, what is assumed and what is out of scope.
2. **scenario** — {name, problem}. Use only the recurring cast: Meridian Logistics (mid-market, many SaaS tools), Aurora Bank (regulated enterprise, strict security review, self-hosting), Pixel & Co. (automation agency). Same customer across related courses.
3. **prerequisites** — the official n8n courses from `prereq`, as {code, title, url}. Link to learn.n8n.io; never copy their content.
4. **concept** — one paragraph, plain words: "but what is X?" for this topic. Then **lessons**: 3–5 items {title, minutes, summary (one sentence)}; minutes add up to the course `minutes`.
5. **by_role[ROLE].say** — how each role talks about it, tied to that role's pain points (see section 4 below).
6. **by_role[ROLE].show** — how it is shown: demo steps or lab steps (numbered, 3–6 steps). Only for roles that demo or build (SE, PARTNER, and AE_ENT when the topic is technical).
7. **objections** — 2–3 {q, a}: real customer pushback and a short, honest answer. **gotchas** — 1–3 things that go wrong in a live call or demo.
8. **practice** — {type, brief, rubric}. Type is "Role-play" (certifications, discovery, objections) or "Hands-on lab" (technical courses). Rubric: 3–4 {criterion, good}.
9. **check** — 3 questions {q, answer}. Answers are one or two sentences. For certifications, the rubric in section 8 is the pass criterion.

Also set: objective (one sentence starting with a verb), status ("Example draft, for review"), updated (YYYY-MM-DD).

## 3. Length and format
- Course: 30–60 minutes as in the catalog; 3–5 lessons; the whole JSON should read in under 10 minutes.
- Talk tracks: 2–4 sentences. Customer emails: subject line + 2–3 sentence summary of the body. Demo/lab steps: 3–6 numbered steps.
- Quiz: 3 open questions with short answers (not multiple choice).
- Labs are done in the learner's own n8n instance and are checked by an automatic grader workflow; describe what the grader checks in the rubric.

## 4. How content changes by role
| Role | say.format | show.format | Focus |
|---|---|---|---|
| AE_MM | Talk track | — | The operational problem and time saved; one discovery question; when not to pitch |
| AE_ENT | Talk track | Demo steps (technical topics only) | Business case, security/compliance/governance, the CTO's concerns |
| SE | Talk track | Demo steps | How it works, limits and prerequisites, a demo flow, an importable example |
| CSM | Customer email | — | Which accounts benefit, adoption play, expansion signal |
| PARTNER | Implementation tips | Lab steps | Best practices, client delivery, certification impact |
Only include roles listed in the course's `roles`.

## 5. Tone and rules
- Plain, professional English. Short sentences. No hype words (revolutionary, seamless, game-changing, unlock, supercharge), no emojis, no exclamation marks.
- Start from the customer's problem, then the product.
- Never invent product facts, numbers, customer names or competitor claims. Anything not certain gets [CHECK WITH PRODUCT] right after the claim.
- Do not copy text from learn.n8n.io or n8n docs; link to them instead.
- Use only the fictional customers above. No real company names.
- Drafts are for human review; nothing is published as final.

## 6. Publishing
For each course: fill templates/course.template.html by replacing __TITLE__ with the title and __COURSE__ with the course JSON (escape "</" as "<\/"), and commit it as courses/<id>.html.
Then add the course id to the `pages` array inside the academy-data JSON block in index.html, so its catalog row becomes a link.
For releases: replace only the HTML between <!--WHATS_NEW_START--> and <!--WHATS_NEW_END--> in index.html. Never regenerate the rest of index.html.
