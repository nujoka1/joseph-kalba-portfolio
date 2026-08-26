# Joseph Nuhu Kalba — Computer Engineering Portfolio

A responsive eight-page personal portfolio completed for **COEN 554 Web Programming, Question 1 (Individual Work)** at Ahmadu Bello University, Zaria.

The visual direction translates the editorial hierarchy, numbered sections, restrained palette and evidence-led presentation observed on [Mauricio Juba's portfolio](https://mauriciojuba.com/) into an original engineering identity. No source code, text, branding or proprietary assets were copied.

## Examination constraints

- Semantic HTML5 only
- One external CSS3 stylesheet
- Flexbox, CSS Grid and media queries
- JSON content model and JSON-LD metadata
- No executable JavaScript
- No framework, CMS, package manager or build step
- Exactly eight assessed HTML pages

## Pages

`index.html`, `about.html`, `education.html`, `skills.html`, `projects.html`, `hobbies.html`, `cv.html`, and `contact.html`.

## Structure

```text
.
├── index.html, about.html, education.html, skills.html
├── projects.html, hobbies.html, cv.html, contact.html
├── assets/css/style.css
├── assets/images/
├── data/data.json
├── docs/technical-report.md
└── .github/workflows/deploy-pages.yml
```

## View locally

The pages can be opened directly, or served over HTTP:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.

## Deployment

The included GitHub Actions workflow deploys the repository root to GitHub Pages after a push to `main`. In repository **Settings → Pages**, select **GitHub Actions** as the source.

Expected URL: `https://nujoka1.github.io/joseph-kalba-portfolio/`

## Portrait

A verified portrait was not available. If desired, place the real approved image at `assets/images/joseph-nuhu-kalba.png`; no substitute face has been generated.

## Report

See [docs/technical-report.md](docs/technical-report.md) for design rationale, architecture, standards, protocol explanation, testing and CMS evaluation.
