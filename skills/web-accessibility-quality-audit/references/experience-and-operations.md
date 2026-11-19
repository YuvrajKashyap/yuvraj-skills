# Whole-site experience and operational checks

Accessibility is central but not the only reason a site can fail a user. Apply this reference to the same representative routes and critical journeys. Keep observations, recommendations, and implementation authority separate.

## Product and information clarity

- State the site’s intended task and audience. Can a first-time visitor understand the offer, next action, price/eligibility/location/hours where relevant, and what happens after contacting or booking?
- Check navigation labels, information scent, page title and headings, scanability, plain language, terminology consistency, visible states, and coherent empty/error/success messaging.
- Verify that visible contact data, hours, prices, address, policies, and calls-to-action agree across site and linked services. Do not “correct” business facts from assumptions; flag discrepancies for the owner.
- Check whether a crucial path requires account creation, download, hover, or a third-party detour unexpectedly. Note fees, privacy handoffs, and whether the user can return to the original site.

## Responsive and browser coverage

- Test at representative narrow phone, large phone, tablet, and desktop widths; include landscape and zoom/reflow. Check navigation, content order, safe-area/notch overlap, viewport-fit, sticky controls, horizontal overflow, and forms under the virtual keyboard.
- Verify touch and keyboard paths independently. Test current major browsers relevant to the audience; do not imply “cross-browser compatible” from one Chromium run. Record exact browser/device or emulator, viewport, and limitations.
- Check light/dark and forced-colors/high-contrast modes if supported or if custom styling could hide information. Test custom fonts failing to load, images failing, and slow connections on critical pages.

## Performance and resilience

- Start with user-visible slowness: page starts, hero/content visibility, input response, layout jumps, resource failures, and long tasks. Use field data when available; lab Lighthouse scores are diagnostic, not production experience.
- Record current Core Web Vitals definitions/thresholds from [web.dev](https://web.dev/articles/vitals) before using numeric targets. Check LCP, INP, and CLS where measurable; distinguish field vs lab, route, device, sample size, and date.
- Check oversized images/video, unexpected autoplay, script and third-party weight, font swaps, blocking resources, and poor caching only when evidence points there. Do not prescribe visible changes as “free” performance fixes.
- Check ordinary resilience: links, 404/500/offline or network failure messaging, useful fallback when APIs or third parties fail, reload/back behavior, and whether a user can recover without losing entered data.

## Findability and discoverability

- Check page titles, descriptions, heading relevance, canonical/robots/sitemap behavior where discoverability matters, and whether public pages are indexable as intended. This is not an SEO guarantee.
- Check link text, broken links, redirects, share previews, and whether linked PDF/media are accessible and current. Avoid publishing or changing metadata in an audit-only task.

## External journey and ownership map

- Map each boundary: embedded booking/checkout, map, chat, consent banner, payment provider, CAPTCHA, authentication, social link, downloadable document, email/phone handoff. Note who owns the surface and whether the user journey crosses domain or opens a new context.
- Test what can be safely tested at each boundary: access, keyboard/pointer traversal, responsive fit, visible handoff, return path, error/recovery, and privacy disclosure. Stop before real submission or irreversible action without authorization.
- Do not assign a third-party defect to the site owner without saying it is vendor-owned; do not omit it from the user-journey report just because it is external. Record the owner’s mitigation path (vendor request, accessible alternative, support channel) as a recommendation.

## Trust, privacy, security, and legal boundaries

- Screen for obvious trust failures: broken HTTPS/mixed content, unexpected sensitive-data collection, secrets visible client-side, unsafe form destinations, stale dependency alerts, missing privacy/consent clarity where trackers/forms exist, and misleading guarantees. Verify before asserting.
- Do not run active penetration tests, fuzz production, bypass auth, scrape private data, or add trackers to inspect them. Escalate security review to `security-best-practices` or a threat-model workflow with explicit scope.
- Do not call a site legally compliant. Laws, contracts, accessibility statements, consent obligations, and retention rules vary by jurisdiction and change; identify the relevant owner/requirement and recommend a specialist review when needed.
- Accessibility overlays/widgets are not evidence of underlying conformance. Test the underlying experience.

## Release and maintenance logistics

- If a change is expressly authorized later: preserve a baseline, make a reversible small change, run tests/build, compare screenshots and tasks, verify in staging, define rollback, then release only with separate authorization if required. Do not conflate “build passed” with “live site works.”
- Leave a repeatable regression inventory: critical routes, states, devices, browser/AT pairs, automated checks, owner, and last verified date. Recheck after component, content, theme, or third-party changes.
- Prioritize issues that block the user’s task, affect many pages through a shared component, or create irreversible harm. Pure polish and speculative optimization follow after blockers.
