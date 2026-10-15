# GTM Academy — concept

Concept of a role-based enablement academy for go-to-market teams, built by Simone Abbiati for the n8n Sales Enablement Manager application. Sample data; not affiliated with n8n GmbH.

Live: https://simoneabbiati.github.io/n8n-enablement-demo/

- `index.html` — catalog. Course data lives in the `academy-data` JSON block; the "Latest release" box sits between `<!--WHATS_NEW_START-->` and `<!--WHATS_NEW_END-->` and is updated by an n8n workflow.
- `templates/course.template.html` — course page; replace `__TITLE__` and `__COURSE__` (JSON) to create `courses/<id>.html`.
- `templates/FRAMEWORK.md` — how every course is written (9 sections, role differences, tone).
- `templates/course-example.GTM101.json` — reference course.
