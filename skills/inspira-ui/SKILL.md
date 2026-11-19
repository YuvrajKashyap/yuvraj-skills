---
name: inspira-ui
description: Integrate an animated Inspira UI component into a Vue or Nuxt application and verify rendering, input, and cleanup.
---

# Inspira Ui

Inspect the component source and the receiving application's Vue version, styling pipeline, client/server boundary, and optional rendering dependencies. Select only the assets and packages the chosen component actually uses.

Mount a minimal version with representative content before integrating it into a full page. In a server-rendered app, keep browser-only initialization in the client lifecycle and reserve space for the initial render. Check that theme variables, canvas size, stacking order, and pointer handling still work inside the real layout.

Navigate away and back. Confirm observers, event listeners, and animation frames are released. Exercise touch and keyboard input, reduced motion, and a slow asset load. Report the specific component and runtime verified.
