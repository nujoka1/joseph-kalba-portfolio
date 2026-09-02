# COEN 554 Question 1 — Technical Report

## 1. Project overview

This project is an eight-page personal portfolio for Joseph Nuhu Kalba, presenting him as a final-year Computer Engineering student working across intelligent software and physical systems. It implements only Question 1 of the COEN 554 examination. The deliverable uses standards-based HTML5, one external CSS3 file, JSON and JSON-LD without executable JavaScript, a CMS or a frontend framework. The content guide defines eight engineering projects, all represented in `data/data.json` and the Projects page.

### Submission scope

The site communicates a single professional identity across eight linked pages: Home, About, Education, Technical Skills, Projects, Hobbies and Interests, Curriculum Vitae, and Contact. The content is intentionally factual and conservative. Unknown dates, qualifications, phone numbers and social profiles remain marked for confirmation rather than being fabricated.

## 2. Design rationale

The primary reference, Mauricio Juba's portfolio, demonstrates oversized editorial typography, compact technical labels, numbered sections, generous spacing and evidence-led case studies. These principles were translated into an original visual system rather than copied. The portfolio uses a warm off-white background, near-black typography and one acid-green accent. Large headings establish identity, while monospace metadata distinguishes categories, technology labels and section numbers. Project descriptions state the prototype, purpose and technologies without inventing performance or deployment claims.

## 3. Information architecture

The site separates its required subjects into Home, About, Education, Skills, Projects, Hobbies and Interests, CV and Contact pages. A consistent header, horizontally usable navigation and footer connect all eight pages. Home provides the narrative overview; deeper pages separate evidence and reduce cognitive load. Relative links support direct local use and GitHub Pages subdirectory hosting.

### File inventory

```text
index.html                 Home and selected project highlights
about.html                 Personal background and working principles
education.html             Academic path and areas of learning
skills.html                Grouped technical capabilities
projects.html              Eight engineering project entries
hobbies.html               Hobbies and interests
cv.html                    Curriculum vitae presentation
contact.html               Contact information and static contact interface
assets/css/style.css       Shared responsive stylesheet
assets/images/             Favicon and approved portrait
data/data.json             Structured content model
docs/technical-report.md   This technical report
submission/README.md       Submission manifest and packaging checklist
```

## 4. Semantic HTML

Each document declares HTML5, English language, UTF-8 and a responsive viewport. Structural elements include `header`, `nav`, `main`, `section`, `article`, `address` and `footer`. Headings follow a meaningful hierarchy. Each page has a unique title and description, the active navigation link uses `aria-current="page"`, and a skip link allows keyboard users to bypass repeated navigation.

## 5. Responsive CSS implementation

`assets/css/style.css` uses a mobile-first cascade. Grid handles page sections, project collections and capability cards; Flexbox handles navigation, tags and metadata. Fluid `clamp()` typography scales without abrupt jumps. Breakpoints at 700px and 1040px progressively introduce multi-column layouts. Navigation remains horizontally scrollable on narrow screens, focus indicators are visible, contrast is strong and motion is reduced under `prefers-reduced-motion`. No inline styles or framework classes are used.

## 6. JSON data structure

`data/data.json` models a `profile` object, agricultural experience, skill groups, project categories and eight project objects. Each project has an ID, title, category, description, technologies and `image_url`. Missing project images or dates use JSON `null`, clearly distinguishing unknown data from empty text. The file is valid JSON and can support a future standards-compliant backend or content workflow, although this static examination implementation does not execute JavaScript to load it.

## 7. JSON-LD

Each page embeds non-executable `application/ld+json` metadata. Schema.org types include `Person`, `ProfilePage`, `CollectionPage`, `ContactPage`, `ItemList` and `EducationalOrganization`. JSON-LD helps search engines interpret the page subject while remaining separate from the visible presentation. It does not manipulate the DOM and therefore respects the no-JavaScript requirement.

## 8. HTTP and HTTPS overview

When a visitor enters the site URL, the browser resolves the host, establishes a connection and sends an HTTP `GET` request. GitHub Pages returns the requested HTML with a status such as `200 OK`. The browser parses that document and sends additional requests for the stylesheet or referenced assets. HTTPS adds TLS encryption and server authentication, protecting content integrity in transit. Static hosting needs no application server for these files, which reduces operational complexity. A missing route normally produces `404 Not Found`, while caching headers can reduce repeat transfers.

## 9. MIME types

- `text/html` tells the browser to parse HTML documents.
- `text/css` identifies the external stylesheet.
- `application/json` identifies `data/data.json` and JSON-LD content.
- `image/png` identifies the expected portrait format when a verified portrait is supplied.

Correct MIME types prevent browsers from guessing how content should be interpreted and improve standards compliance and security.

## 10. Testing and validation

Validation covers the exact count of eight root HTML pages, relative internal links, local asset references, JSON syntax, every JSON-LD block, required semantic elements, unique titles, viewport metadata and active navigation state. Repository searches check for prohibited JavaScript/TypeScript files, framework scaffolding, inline styles and executable scripts. Layout CSS includes mobile, tablet and desktop states plus keyboard focus and reduced-motion support. The site is also served through a simple HTTP server and requested as a browser would request static files.

The final local checks completed for this submission were:

```bash
find . -maxdepth 1 -name '*.html' | wc -l
jq empty data/data.json
python3 -m http.server 8765
curl --fail -I http://127.0.0.1:8765/index.html
curl --fail -I http://127.0.0.1:8765/projects.html
curl --fail -I http://127.0.0.1:8765/assets/images/joseph-nuhu-kalba.png
```

The expected results are eight HTML pages, successful JSON parsing, and `200 OK` responses for the two updated pages and the portrait asset. Editor diagnostics also report no errors in the touched HTML, CSS or JSON files.

## 11. Accessibility, security and maintainability

The pages use landmark elements, a skip link, meaningful heading order, descriptive page metadata and visible keyboard focus states. Navigation marks the current page with `aria-current`, while the portrait has alternative text. The stylesheet includes a reduced-motion preference and responsive layouts that avoid horizontal page overflow.

The static architecture has no server-side credentials, database connection, login form or executable client script. Contact is provided through a `mailto:` link; the page does not falsely claim that its static form sends messages. External links are limited to the candidate's GitHub profile and email address. Repository access and GitHub Pages deployment permissions remain operational responsibilities.

## 12. Deployment procedure

The repository includes `.github/workflows/deploy-pages.yml`. On a push to `main`, GitHub Actions checks out the source, configures Pages, uploads the repository as a static artifact and deploys it. The repository Pages source must be set to GitHub Actions. No compilation, `npm install` or development server is required.

### Live deployment

The deployed portfolio is available at [https://nujoka1.github.io/joseph-kalba-portfolio/](https://nujoka1.github.io/joseph-kalba-portfolio/). A direct HTTP check returned `200 OK` for the public homepage on 2 September 2026. The deployment is served over HTTPS by GitHub Pages.

## 13. CMS evaluation (436 words)

A manual HTML/CSS/JSON architecture is preferable for this portfolio because the content set is small, the page structure is stable and the author is technically capable of editing source files. Static files are easy to inspect, version and deploy. They can be served directly by a content delivery network without database queries, server-side rendering or plugin execution. This usually produces fast initial responses and a small hosting footprint. The limited runtime surface also reduces security exposure: there is no administrative login, database or plugin ecosystem to patch. Security still matters—repository access, deployment permissions and third-party links must be protected—but the number of moving parts is low.

WordPress solves a different problem. It provides an administration interface, themes, plugins, media management, revision tools and roles for non-technical editors. Those capabilities become valuable when content changes frequently, several people publish independently, approval workflows are needed, or the organisation cannot depend on a developer for routine updates. A department publishing news every week, maintaining many staff profiles and delegating content to administrators could justify a CMS. The cost is additional infrastructure and governance: WordPress core, themes and plugins require updates; database backups and recovery must be managed; accounts need least-privilege access and strong authentication; and poorly maintained extensions can expand the attack surface.

Maintenance differs in both models. In the static site, a content update requires editing HTML or JSON, validating the change and deploying through Git. This creates a strong audit trail but imposes a technical barrier. Repeated content may also become harder to keep consistent as the number of pages grows because this examination prohibits generators and executable scripts. In WordPress, a non-technical editor can update content through forms, but the platform itself becomes a maintained software product. Performance can remain good with caching, image optimisation and careful hosting, yet a dynamic CMS normally needs more resources than serving static files.

Team size and update frequency should drive migration, not fashion. For one technical owner, eight pages and occasional updates, static architecture is simpler, faster and easier to verify. Migration becomes defensible when there are multiple non-technical contributors, daily or weekly publishing, hundreds of entries, scheduled content, editorial approvals, localisation, advanced search, or a need to manage media at scale. Even then, the team should compare a traditional WordPress installation with a controlled headless approach and assess hosting, training, backups, accessibility and security responsibilities. For the present portfolio, WordPress would add operational cost without improving the assessed outcome.

## 14. Conclusion

The portfolio meets the Question 1 content and technology scope with a maintainable static architecture and an original responsive design. Remaining factual placeholders are limited to exact qualification details and detailed employment dates or titles. Those facts should be confirmed before inclusion rather than inferred.

