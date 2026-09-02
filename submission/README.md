# COEN 554 Question 1 Submission

**Candidate:** Joseph Nuhu Kalba  
**Programme:** B.Eng. Computer Engineering  
**Institution:** Ahmadu Bello University, Zaria  
**Question:** 1 — Personal Portfolio Web

## Deliverables

| Item | Location | Purpose |
| --- | --- | --- |
| Portfolio website | Repository root | Eight linked HTML5 pages, one external CSS3 stylesheet, JSON data and JSON-LD metadata |
| Technical report | `docs/technical-report.md` | Design rationale, architecture, standards, HTTP/HTTPS, MIME types, testing and CMS evaluation |
| Content model | `data/data.json` | Structured profile, skills, agricultural experience and eight projects |
| Approved portrait | `assets/images/joseph-nuhu-kalba.png` | Candidate portrait used on the homepage |
| Live deployment | `https://nujoka1.github.io/joseph-kalba-portfolio/` | Public GitHub Pages site, verified with `200 OK` |
| Deployment workflow | `.github/workflows/deploy-pages.yml` | GitHub Pages deployment configuration |

## Website pages

`index.html` · `about.html` · `education.html` · `skills.html` · `projects.html` · `hobbies.html` · `cv.html` · `contact.html`

## Verification checklist

- [x] Question 1 portfolio scope implemented.
- [x] Eight assessed HTML pages included.
- [x] Internal navigation uses relative links.
- [x] One external CSS3 stylesheet is used.
- [x] No executable JavaScript or frontend framework is included.
- [x] JSON content model parses successfully.
- [x] JSON-LD metadata is embedded in the pages.
- [x] Responsive, keyboard-focus and reduced-motion CSS states are included.
- [x] Unverified facts remain marked for later confirmation rather than invented.

## Create the final ZIP

Run this command from the repository root. It excludes Git history and generated archive files while preserving the website root structure:

```bash
zip -r ../joseph-kalba-coen554-question1-submission.zip . \
  -x '.git/*' '.gitignore' '*.zip' '*.DS_Store'
```

Open `index.html` from the extracted archive or serve the extracted root with `python3 -m http.server 8000` before submission.