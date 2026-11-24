# Switching frontends

Keep a registry with a stable slug, display name, premise, and entry point for each option, including the original. Add lightweight entries first so the picker stays usable while each direction is built. Share validated content, authentication, and business operations. Scope styles by module or root selector, including baseline styles that can remain loaded after navigation.

- **Single-page app.** Let the existing public route render the active entry. Mount previews under a separate prefix such as /d/<slug>/ and give internal links their preview base path. Lazy-load directions individually. Return a clear missing-preview state for unknown slugs.
- **File-based router.** Keep the existing route tree in place while exploring. Add a preview route that resolves the slug and remaining path through the registry. Preserve server/client boundaries and verify that refreshing a nested preview resolves the same screen.
- **Static site.** Build each option under its own preview prefix. Use the build configuration to select the entry published at the root. Test asset URLs and direct navigation from a nested page.
- **Mobile or desktop app.** Use a development menu, launch argument, or build flag to choose the root view. Keep navigation and stored data compatible when switching.

Check a deep link, a form validation failure, and a successful test action in two different directions. Switch back to the baseline and verify its route and styling. Document the active setting and keep preview routes within the intended review environment.
