# Testing and reporting protocol

## 1. Establish a truthful scope

Record site/repo and revision or deployment URL if known; audit date; pages and states; critical tasks; viewport/device/browser; access method; applicable standard target; whether production/staging/local; and any constraints. Name what is out of scope. If the site is live, avoid actions that mutate business state.

Use W3C [WCAG-EM 2](https://www.w3.org/WAI/test-evaluate/conformance/wcag-em/) as the model for systematic sampling: define scope, explore the product, select representative views, evaluate, report. For an 80/20 audit, state that the sample is triage, not a conformance evaluation.

## 2. Sample by risk, not URL count

Inventory page templates and interaction patterns. Prefer these over ten near-identical pages:

1. Entry page with primary navigation and call-to-action.
2. One long/content-rich page and one repeated component-heavy page.
3. The highest-value journey from entry to completion boundary: contact, booking, purchase, signup, or application.
4. Mobile menu, open dialog, expanded accordion, carousel, validation error, success, loading, empty and failure states.
5. External provider handoff and downloadable document if central to the journey.
6. At least one edge combination: narrow viewport + zoom, keyboard + dialog, screen reader + form error, reduced motion + animated route.

If a shared component fails, sample where it appears and estimate reach. Never report sitewide pass from a sampled page.

## 3. Use complementary evidence

| Method | Good for | Cannot establish alone |
| --- | --- | --- |
| Source/DOM inspection | Semantics, labels, structure, likely cause | Rendered behavior, user experience, production parity |
| Automated scan (axe, Lighthouse, etc.) | Common machine-detectable defects and regression | Full WCAG conformance, keyboard usability, alt-text quality, real screen-reader experience |
| Keyboard-only traversal | Focus order, traps, activation, hidden controls, handoffs | Screen-reader announcements, all motor/vision needs |
| Screen reader and accessibility tree | Names/roles/states, reading order, announcements | Every AT/browser combination or all disabilities |
| Contrast/zoom/responsive manual checks | Visual legibility, clipping, reflow, target usability | All visual and cognitive needs |
| User testing with disabled participants | Real task friction and workarounds | Formal conformance or all users from a tiny sample |
| Field performance/analytics | Real-world distributions | Root cause or unmeasured user segments |

Run automated checks on *states*, not only the initial DOM. Verify reported failures; log false positives and suppressions with reasons. Use role/name assertions and journey tests where automation is appropriate. Do not silently auto-fix production findings.

## 4. Manual test scripts

### Keyboard script

1. Reload and start before first control. Press Tab through every visible and revealed control; Shift+Tab back. Note first target and focus visibility.
2. Activate nav/menu, modal, accordion, carousel, form, and critical CTA with Enter/Space as appropriate. Use Escape to close dismissible layers and verify focus returns sensibly.
3. Observe whether focus is trapped only where intended, whether background focus is inaccessible during modal use, whether sticky UI hides focus, and whether hidden controls receive focus.
4. Complete the journey up to a non-mutating boundary. Record the exact step at which mouse-free use fails. No mouse movement during this test.

### Visual/adaptation script

1. Check text and UI contrast in default, focus, hover, error, disabled, and overlay states, including backgrounds under translucent layers.
2. Increase text to 200%; test 320 CSS-px-equivalent reflow and representative phone/tablet/desktop widths. Observe clipping, horizontal scrolling, hidden or overlapping controls, and content order.
3. Enable reduced motion; inspect animation and auto-moving content. Try landscape and touch, if available.
4. Review color-dependent information with color cues removed or simulated, then verify explicit redundant cues. Simulation alone is inconclusive.

### Assistive-technology script

1. State the screen reader and browser. Navigate by landmarks/headings, links/buttons, and form fields. Check whether their names and order match the visual task.
2. Open a dynamic component, trigger validation, and confirm status and error announcements. Test focus after opening/closing and after route/state changes.
3. Record uncertainty if no screen-reader session was actually completed. Do not rename an accessibility-tree inspection as “screen-reader tested.”

## 5. Severity and prioritization

- **P0 critical:** Critical journey impossible or dangerously misleading for an affected group; irreversible loss/financial/safety risk; no usable workaround. Escalate immediately.
- **P1 high:** Core task blocked or materially impaired, widespread shared-component issue, or serious WCAG failure in important content.
- **P2 medium:** Significant friction with workaround, or narrower/non-core WCAG failure.
- **P3 low:** Minor usability/polish, best-practice improvement, or isolated inconvenience.

Adjust for reach, frequency, task importance, user impact, and confidence. A criterion label is not a severity score; low contrast on a primary CTA may matter more than an isolated decorative alternative-text issue. Give an 80/20 sequence: blockers and shared-component fixes first, then content/state gaps, then polish. Do not bury blockers under a long undifferentiated checklist.

## 6. Finding record

For each item capture:

- ID and concise user-centered title.
- Status: **observed**, **code-indicated**, **unverified**, or **resolved-and-regression-tested**.
- Severity and reach; affected users/tasks; route, state, viewport, browser/AT.
- Reproduction steps with expected and actual behavior; screenshot/log/selector/line link as appropriate.
- WCAG criterion and level only when supported; otherwise label as usability/best practice/operational risk.
- Recommended outcome and acceptance test, owner (site, vendor, content, legal, security), and confidence/unknowns.

## 7. Report template

Start with a one-sentence verdict. Then give a compact table or bullets for the top 3–7 findings, ordered by user impact. Include “tested” and “not tested,” then a sequenced next-action list. When asked yes/no, answer yes/no first with the qualifying scope.

Example wording:

> In the tested homepage and booking handoff, I found a keyboard blocker in the mobile menu. I did not test the final booking submission or any screen reader, so I cannot say the full site meets WCAG 2.2 AA. No site changes were made.

Never report “100% accessible,” “fully compliant,” or “all bases covered” without a properly scoped, qualified evaluation—and even then describe version, level, pages/states, technology assumptions, date, and known limitations. A Lighthouse score is a diagnostic metric, not a certificate.
