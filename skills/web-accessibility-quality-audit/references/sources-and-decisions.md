# Source and synthesis ledger

Reviewed 2026-09-17. Refresh dynamic guidance before a consequential or formal audit. This file records why guidance was adopted; it is not a copied standard.

## Primary standards and evaluation sources

| Source | Adopted use | Boundary |
| --- | --- | --- |
| [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/) | Normative success criteria, A/AA/AAA distinction, current practical review target | Legal applicability is not inferred; read exact criteria and exceptions. |
| [W3C WCAG-EM 2 overview](https://www.w3.org/WAI/test-evaluate/conformance/wcag-em/) | Scope → explore → representative sample → evaluate → report; formal evaluation route | Quick triage is not formal conformance. WCAG-EM adds no new WCAG requirements. |
| [W3C Easy Checks](https://www.w3.org/WAI/test-evaluate/preliminary/) | Fast manual first pass: title, images, headings, contrast, keyboard, zoom, labels | Preliminary review cannot establish conformance. |
| [W3C evaluation tools](https://www.w3.org/WAI/test-evaluate/tools/) | Automated checks supplement manual evaluation | Tools can be inaccurate and cannot test all issues. |
| [W3C involvement of users](https://www.w3.org/WAI/test-evaluate/involving-users/) | Real task testing catches barriers beyond checklists | A small user sample does not represent all disabilities. |
| [WAI ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/) | Expected semantics and keyboard patterns for custom widgets | Native HTML remains preferable when suitable. |
| [WAI accessibility principles](https://www.w3.org/WAI/fundamentals/accessibility-principles/) | Cross-disability framing, including color, resizing, structure, predictability | Overview, not exhaustive test criteria. |

## Specialist operational sources

| Source | Adopted use | Boundary |
| --- | --- | --- |
| [Playwright accessibility testing](https://playwright.dev/docs/accessibility-testing) | Automated checks can target interactive states; manual and inclusive testing remain necessary | Do not install tooling or edit tests during audit-only work. |
| [Chrome Lighthouse scoring](https://developer.chrome.com/docs/lighthouse/accessibility/scoring) | Scores summarize a subset of weighted automated audits | Manual checks are absent from score; no certification. |
| [web.dev Web Vitals](https://web.dev/articles/vitals) | Current performance metrics and field/lab distinction | Metrics/thresholds can change; verify at audit time. |
| [OWASP Top 10](https://owasp.org/projects/top-ten) | Screen and route obvious web security risks to specialist review | This skill does not perform penetration testing or certify security. |

## Local-skill synthesis

- `skill-synthesis`: used its candidate screening, independent-source comparison, and rejection ledger. Avoided installing unknown remote skills or running remote scripts.
- `skill-creator`: used short frontmatter/entrypoint and task-specific reference files with validation.
- `web-design-guidelines`: retained as a live, separate UI-code review skill instead of copying a potentially stale ruleset here.
- `webapp-testing`, `mobile-frontend`, `verification-before-completion`, `frontend-design`, `invisible-performance`, `security-best-practices`: sampled for complementary testing, adaptation, evidence, performance, and security boundaries. Imported only generalizable audit practices, not their implementation mandates.
- `find-skills`: discovery was considered, but popularity/install count is not evidence of standards correctness; official W3C and original tool documentation were preferred for technical claims.

## Rejected shortcuts

- One automated scan, Lighthouse score, or browser screenshot as an accessibility verdict.
- “Color-blind safe” based only on palette simulation; explicit non-color cues and contrast are checked instead.
- Requiring 44×44 px as if it were WCAG 2.2 AA; the normative minimum has exceptions and a different threshold.
- Treating WCAG 2.2 AA as automatically legally required everywhere.
- Auditing only the first page, default state, or owned domain while ignoring the journey’s third-party handoff.
- Active tests on a production booking/contact/payment flow without authorization.
- Turning an audit request into code, design, deployment, tracker, or vendor changes.
