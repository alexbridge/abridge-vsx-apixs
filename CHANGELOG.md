# Changelog

## [1.9.0]

### Added
- Scripts: `pm.*` snippet completions in the pre/post script editor. Type a name fragment (`info.it`); Enter replaces the typed text with the snippet. Inside a string literal, only the name is inserted.

### Fixed
- Runner: stopping a run no longer records the aborted in-flight request as a failed result.
- Runner: the Runner leaves the running state when a run throws before completing.

## [1.8.1]

### Added
- Scripts: `Format` button in the pre/post script editor reformats JavaScript.
- Scripts: `pm.sendRequest` accepts a `timeout` option in milliseconds.
- Collections tree: `Ctrl+Up` / `Ctrl+Down` move the selected collection, folder, or request.
- Collections tree: reopening a workspace reveals the last opened request, expanding its folders.
- JSON body: pasting into a string literal escapes the pasted text.
- Runner: the tab icon show progress and finish icons.

### Changed
- Inspect tab: JSON request and response bodies render indented.

### Fixed
- Scripts: an error caught inside a `pm.sendRequest` `try/catch` no longer fails the request.
- Scripts: an uncaught error in a pre-request script aborts the send.
- Scripts: `pm.variables` set in a collection pre-request script resolve when sending a request on its own.
- Scripts: `pm.request.body` is an object with `.raw`, matching Postman.

## [1.8.0]

### Added
- Script tests: `pm.expect` and `pm.test` results render above the response tabs.
- Script snippet bar: inserted snippets support tab stops.
- Requests: `User-Agent` header defaults to the current APIxs version.

### Fixed
- Responses: binary data detection uses buffer bytes, ignoring `Content-Type`.
- Dragging a folder or request across collections moves the item instead of deleting it.
- Percent-encoded dynamic variables like `{{$guid}}` in the URL resolve before sending.

## [1.7.0]

### Added
- Folders export as Postman collections.
- Requests support abort cancellation.
- Script runner awaits promises.
- Script runner aborts on error.
- Script runner enforces execution timeout.

### Fixed
- Request path faker generates correct values.
- Collections tree supports drag and drop restoration.
- URL variable placeholders containing dots or slashes do not split into separate host/path segments.

## [1.6.0]

### Added
- **Runner** — allow run iterations in parallel.

## [1.5.0]

### Added
- **Inspector Trace** — Full execution visibility for pre/post request scripts.
- **Body Streaming** — `pm.response.stream` buffered stream of response
- **Enhanced Fuzzy Match** — Improved search for scripts, variables, and autocomplete.
  **Inline Editing** — Direct renaming of requests and folders in the request page.

## [1.4.0]

### Added
- **Import from cURL** — inject environment variables placeholders, eg `{{host}}` for environment variables values.

## [1.3.0]

### Added
- **Faker locale setting** — `apixs.faker.locale` drives `{{$random*}}` (names, IBAN, etc.).
- **Export Request to cURL** — right-click → copy resolved cURL.

## [1.2.0]

### Added
- **Collections Quick Filter** — filter tree by folder path; comma for OR.
- **Filter history** — last 10 saved in `.apixs/filters.json`.

## [1.1.0]

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
