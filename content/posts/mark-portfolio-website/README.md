# Mark Grover — Personal Portfolio Website

A responsive, data-driven personal portfolio built with vanilla HTML, CSS, and JavaScript — no frameworks, no build tools, no auto-generated code.

**Live site:** [markjgrover.com](https://markjgrover.com)

---

## About This Project

This portfolio was built hands-on using VS Code, a browser, and LLMs as a thought partner — not as a code generator. Every line of HTML, CSS, and JavaScript was written and assembled by me. The LLMs helped me think through architecture, debug edge cases, and explore UX ideas — but the implementation decisions, structure, and actual code were mine.

The result is a site that loads fast, requires zero dependencies to run, and is entirely maintainable without a build pipeline.

---

## Features

### Role-Based Personalization
The site supports a `?role=` URL parameter that tailors the entire experience — hero copy, featured portfolio projects, relevant certifications, and testimonials — to a specific audience. This means a single URL can be shared in a job application and present a focused, role-relevant story.

Supported roles:
- `?role=pm` — Sr. Program Manager
- `?role=ux` — UX Program Manager
- `?role=enablement` — Sr. Technical Enablement
- `?role=sre` — Site Reliability Engineer
- (default) — All Roles view

### Data-Driven Architecture
All content — portfolio projects, certifications, testimonials, impact metrics, role copy — lives in a single `data/portfolio.json` file. The JavaScript reads it on load and renders the UI dynamically. Adding or updating content requires editing only the JSON.

### Skill-Based Portfolio Filtering
Clicking a skill tag in the Skills section highlights and reorders portfolio cards to surface projects that demonstrate that skill. A "Return" button restores the previous scroll position after filtering, preserving context.

### Impact Metrics Section
A grid of key career metrics (e.g., "119,000+ Global Learners Reached") that are role-aware — relevant metrics are visually emphasized when a role is selected. Each metric links to the related portfolio case study.

### Project Case Study Modals
Each portfolio card opens a modal with the full case study: challenge, role, actions taken, measurable results, skills demonstrated, and tools used.

### Certifications Section
Credentials are organized into three tiers — Featured, Supporting, and Foundational/Historical — and sorted by relevance to the selected role. Historical credentials are collapsed by default.

### Testimonials Carousel
A responsive carousel with swipe support on mobile. Testimonials are sorted by role relevance when a role is selected.

### One-Time Onboarding Hint
First-time visitors see a tooltip pointing to the role selector. Dismissed state is stored in `localStorage` so it only appears once.

### Accessibility & UX Details
- Scroll spy highlights the active nav section
- Back-to-top button appears after scrolling past the viewport height
- Mobile hamburger nav with smooth open/close
- Modal scroll-lock with focus restoration on close
- Keyboard `Escape` closes the modal
- `aria-hidden`, `aria-label`, and `role="dialog"` throughout
- Email copy-to-clipboard with visual feedback

### Analytics
Lightweight Google Analytics integration tracks role views and resume downloads by role.

---

## Project Structure

```
staging/
├── index.html              # Single-page shell; all sections are empty containers
├── css/
│   └── styles.css          # All styling — layout, components, animations, responsive
├── js/
│   └── main.js             # All behavior — data loading, rendering, interactions
├── data/
│   └── portfolio.json      # All content — roles, projects, skills, certs, testimonials
└── assets/
    ├── badges/             # Certification badge images
    ├── images/             # Headshot and background images
    ├── testimonials/       # Testimonial headshot images
    ├── Mark-Grover-Resume.pdf
    └── Mark-Grover.vcf     # vCard for contact download
```

---

## How It Works

On page load, `main.js` fetches `portfolio.json` and stores all data in module-level variables. It then reads the `?role=` URL parameter (defaulting to `pm`) and calls `applyRole()`, which is the single orchestration function that re-renders every section of the page.

```
loadPortfolioData()
  └─ applyRole(role)
        ├─ renderRoleContent()      // Hero headline + about text
        ├─ renderImpact()           // Impact metric cards
        ├─ renderCards()            // Portfolio project cards
        ├─ renderSkills()           // Skill tag list
        ├─ renderTestimonials()     // Testimonial cards
        ├─ renderCertifications()   // Cert tiers
        ├─ updateCredentialSummary()
        ├─ renderRoleDropdown()
        └─ initOnboarding()
```

When the role dropdown changes, `applyRole()` is called again with the new role — no page reload, no routing library needed.

---

## Running Locally

No build step required. Serve the `staging/` directory with any static file server:

```bash
# Python
cd staging
python3 -m http.server 8080

# Node (npx)
cd staging
npx serve .
```

Then open `http://localhost:8080`.

> **Note:** The site fetches `data/portfolio.json` via `fetch()`, which requires a server — opening `index.html` directly as a `file://` URL will fail due to CORS restrictions on local file reads.

---

## Customizing Content

All content is in `data/portfolio.json`. The top-level keys are:

| Key | Description |
|---|---|
| `roles` | Per-role headline, about text, label, and resume path |
| `impactMetrics` | Career impact stats with icon, value, label, and linked project |
| `portfolio` | Project cards with full case study details and role/skill tags |
| `certifications` | Credentials with tier (`primary`, `supporting`, `historical`), role tags, and badge image |
| `testimonials` | Quotes with role tags, name, title, company, and headshot |
| `credentialSummaries` | Short per-role credential summary text |

---

## Philosophy

This project was deliberately built without a framework, bundler, or component library. The goal was to stay close to the platform — understanding exactly what the browser is doing at every step — while using LLMs as a collaborative problem-solving tool rather than a code dispenser.

The result is a site with no `node_modules`, no build output to maintain, and no abstraction layers between the code and the browser. It's fast, portable, and easy to reason about.

---

## Contact

- **Email:** mark@markjgrover.com
- **LinkedIn:** [linkedin.com/in/markjgrover](https://www.linkedin.com/in/markjgrover/)
