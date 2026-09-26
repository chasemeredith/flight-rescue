# Flight Rescue source handoff

Recovered from Apollo on 2026-09-26 for private review and handoff to the original creator. No license grant is added; existing ownership and asset rights still apply.

## Download the source

Download [flight-rescue-source.zip](flight-rescue-source.zip) and extract it. The archive contains the complete source tree described below, including both engine versions, all preserved website variants, tests, and sample configuration. `SOURCE_MANIFEST.json` records the source checksums.

Archive SHA-256: `cd90d3a34833453fadb69a5f9443dbdc098ce0a0b853cb043bfb724b3d1609fa`.

## Contents and provenance

- `source/flight-rescue-site-simple`: latest dated simplified website variant; source and build/check scripts.
- `source/flight-rescue-site-v2`: richer landing page, waitlist, Python preview server, Netlify functions, assets and legal-page drafts. Historical `snapshots/` retained.
- `source/flight-rescue-site`: original website prototype.
- `source/flight-rescue-site-v2-backups`: three dated design variants.
- `source/flight-rescue-site-v2-snapshot-before-full-redesign`: earlier complete design variant.
- `source/engine-flightrescue`: Flight Rescue profile's `skills/travel/flight-travel-operations` skill, references, deterministic flight-risk engine, turbulence helper and tests.
- `source/engine-shared`: separate shared Hermes/iCloud flight skill, engine and references. Preserved independently because the shared and profile versions differ; neither silently replaces the other.

Website directory names match their Apollo home-directory source names. Engine source paths were the flightrescue profile's skills/travel directory and the shared `.hermes/skills/travel` directory respectively. No whole Hermes profile or unrelated skills were copied.

## Status and limitations

This is recovered source, not a complete production service. Legal pages, contact addresses, product claims and deployment targets are historical and need creator review. `security.txt` uses a placeholder contact. A personally tailored skill sentence was generalized. Product contact mailboxes remain as historical source content; their ownership and availability were not verified.

Apollo's final shadow-beta summary explicitly reported an incomplete run: 69 selected, 62 resolved, 7 pending, estimated AeroAPI spend $1.21, and one missed major disruption. These results do not establish predictive reliability. No passenger data, cohort rows, database, runtime events, customer lists or sessions are included. External API credentials, messaging/payment services, deployment configuration and any 1Password bridge must be configured separately.

## Local verification

Python engine tests passed: 41 profile tests and 27 shared-version tests. Run from repository root:

```sh
python3 -m unittest discover -s source/engine-flightrescue/scripts -p 'test_*.py'
python3 -m unittest discover -s source/engine-shared/scripts -p 'test_*.py'
```

The simple website can be built using `python3 source/flight-rescue-site-simple/scripts/build.py`, or its static pages opened directly. Review the v2 build scripts and Netlify configuration before deployment. The v2 Python server reads SITE_USER/SITE_PASSWORD; `.env.example` documents sample values but is not automatically loaded. Engine defaults may write local databases under the user's `.hermes/data` directory: use explicit temporary database paths for experiments. No external service, paid API, publication or deployment was performed during extraction.

## Exclusions and sanitization

Excluded remote `.preview.env`, `.netlify/`, `dist/`, node_modules, caches, logs, CSV test data, zipped builds and all Hermes sessions, customer/subscriber data, databases, runtime state and unrelated skills. Credentials were not transferred. Replaced the Apollo personal security contact with `security@example.com`; replaced the named personal styling preference with a traveler-neutral one. Historical source duplicates are intentional provenance, not generated build copies.

`SOURCE_MANIFEST.json` records included source files with SHA-256 checksums. Focused text checks found no private-key blocks or common provider-token patterns; credential references reviewed in code use environment variables. This is a focused source review, not a guarantee that every possible secret format is detectable. The extraction step did not change the Apollo originals.
