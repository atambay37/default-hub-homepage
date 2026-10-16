# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

- **Symposium attendees.** Researchers at the Schmidt Observatory System Science Symposium who sign in during the event to do hands-on work (tutorials, workshops, hack time) in prepared notebooks.
- **Organizers and instructors.** People who prepare those materials before the event and support attendees during it. Hub admins also get a shared `allusers` directory for distributing materials.

The login page is the first thing both groups see. They arrive with a shared event password and want to get into a working environment immediately.

## Product Purpose

A 2i2c-operated JupyterHub for the **Schmidt Observatory System Science Symposium**, the official event hub funded by Schmidt Observatory System. Success means an attendee enters the shared password and lands in a ready-to-use environment with no setup. The hub is for the event only and winds down after the symposium.

## Positioning

The symposium's own compute environment. It comes preloaded with access to Schmidt Observatory System data and tools, so attendees work on the real system's data during the event rather than on a generic hub.

## Operating Context

- Sign-in uses JupyterHub's `shared-password` authenticator: a username plus the shared event password, with no OAuth provider.
- Users land in JupyterLab (`defaultUrl: /lab`). RStudio is also offered.
- The `schmidt-observatory-system` S3 bucket is mounted into user environments.
- LLM API keys are provisioned per user through a LiteLLM key provisioner.
- Git operations against GitHub go through a GitHub App credential helper.
- Hub config lives in [2i2c-org/infrastructure](https://github.com/2i2c-org/infrastructure) at `config/clusters/schmidt-astro-events/`. The homepage template vars (org name, logo, URLs, operated/funded/designed by) come from `common.values.yaml` under `jupyterhub.custom.homepage.templateVars`.

## Capabilities and Constraints

- This repo holds Jinja2 templates that override JupyterHub's defaults. `templates/login.html` extends JupyterHub's own `templates/login.html` and must keep its blocks (`login_container`, `stylesheet`, `script`) and the `custom.redirect_to` redirect logic working.
- Built against JupyterHub 5.x (Bootstrap 5). JupyterHub sets the light or dark theme through `data-bs-theme`, so pages must work in both.
- Static assets are served from `extra-assets/` via `static_url('extra-assets/...')`.
- The branch name `schmidt-astro-events` maps this customization to the `schmidt-astro-events` hub. Changes reach the hub within about 5 minutes of a push.
- The `login_container` block renders the username/password form for this hub, not a single sign-in button.
- **Page copy is to be rewritten for the event.** The current FAQ text is 2i2c's generic default (e.g. "open to instructors and students", "proof-of-concept service") and is not accurate for this hub. The user will supply or approve the replacement wording; do not invent it.

## Brand Commitments

- This is Schmidt Observatory System's **official event**, so their name and logo are in use with that standing.
- The org name is exactly "Schmidt Observatory System Science Symposium". The parent organization is "Schmidt Sciences" (two words, plural), never "Schmidt Science" or "Schmidt Futures".
- Look and feel follow the event website, https://symposium.schmidtobservatorysystem.org/. The visual system built from it is recorded in `DESIGN.md`.
- Copy taken from the event site is limited to what the user approved: the fact line "November 3–5, 2026 / Florence, Italy". The site's other copy, including the "An initiative of Schmidt Sciences" co-brand, is not used without approval.
- 2i2c is credited as operator and designer; the 2i2c infrastructure footer stays.

## Evidence on Hand

- Org logo: `https://symposium.schmidtobservatorysystem.org/static/assets/logo-nav.png` (from the hub template vars).
- Reversed (white) org logo: `extra-assets/images/sos-logo-white.png`, from the event site, with its origin embedded in the file.
- Event site: https://symposium.schmidtobservatorysystem.org/
- Event dates and place, from the event site: November 3–5, 2026, Florence, Italy.
- **Not on hand:** the hub-specific agenda or sessions, attendee instructions, password distribution details, and approved event copy for the FAQ. Do not fabricate any of these.

## Product Principles

1. **Get attendees working fast.** Sign-in is the primary action and stays above everything else on the login page.
2. **It's the symposium's hub, not a generic one.** Content and copy speak to this event and Schmidt Observatory System data, not to 2i2c hubs in general.
3. **Accurate over filler.** Unknown event facts stay out until the organizers provide them.
4. **Don't break the hub.** Template changes preserve JupyterHub's login behavior, redirects, and both themes.

## Accessibility & Inclusion

Inferred, not separately confirmed: target WCAG 2.x AA contrast (body text at least 4.5:1, large text at least 3:1). Attendees may sign in on laptops or phones at the venue, so the login form must work at phone width.
