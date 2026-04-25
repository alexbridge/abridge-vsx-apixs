# Changelog

All notable changes to APIxs will be documented here.

## [1.3.0] - 2026-04-25

### Added
- **Faker locale setting** — `apixs.faker.locale` drives `{{$random*}}` (names, IBAN, etc.).
- **Export Request to cURL** — right-click → copy resolved cURL.

## [1.2.0] - 2026-04-21

### Added
- **Collections Quick Filter** — filter tree by folder path; comma for OR.
- **Filter history** — last 10 saved in `.apixs/filters.json`.

## [1.1.0] - 2026-04-17

### Added
- **Paste from cURL** — right-click a folder or collection → *Paste from cURL* → parses clipboard into a new request. Handles method, URL, headers, body (raw/form-data/urlencoded), Bearer/Basic auth, and query params.
- **Runner: Recent Data Files** — last 10 CSV data files are remembered per workspace. One click to reload; missing files are flagged and auto-pruned.
- **Export to Postman** — right-click a collection → *Export as Postman Collection* → save as Postman v2.1.0 JSON. Round-trip with Postman confirmed.
- **Image & PDF Response Preview** — image responses render inline in the response viewer; PDFs open in the OS viewer via a single button.
- **Sort JSON Response by Keys** — toggle button on JSON responses; affects pretty view, copy, and save.
- **Script Snippet Bar** — bottom bar below all pre/post script editors with fuzzy search over 70+ `pm.*` snippets (tests, assertions, response, environment, variables, globals, flow control, crypto, etc.).
- **Auto Schema Prepend** — URLs without a scheme now auto-prepend `http://` (when port is set and ≠ 443) or `https://` (otherwise), matching Postman behavior.
- **Inspect Tab on Failed Requests** — even when a request errors out, the resolved URL/headers/body are now viewable in the Inspect tab.

### Changed
- **Output Panel: Log Level Filter** — the Apixs Output channel is now a `LogOutputChannel`, adding a native log-level filter (Info / Warning / Error / Debug / Trace) and auto-timestamps. Script `console.log` / `console.warn` / `console.error` are now filterable separately.

### Fixed
- **Runner: `pm.variables.set()` now persists across iterations** — matches Postman behavior. Previously, local variables set via `pm.variables.set()` were reset at the start of each iteration, breaking counters and accumulators across a run. Local scope now lives for the duration of the entire collection run, as documented by Postman.

### Security
- **Import trust prompt** — when importing a Postman collection that contains pre-request or post-response scripts, APIxs now warns the user and requires explicit confirmation. Scripts are arbitrary JavaScript that runs on your machine; only import collections from sources you trust. The prompt also offers to open the raw JSON for review before import.
