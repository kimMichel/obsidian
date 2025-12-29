"Absolute path bypass" is when an application tries to restrict file access to a safe folder, but an attacker supplies an **absolute path** (a full filesystem path) so the restriction is bypassed.

It's usually part of [[Path traversal]] / File path injection bugs.

# What it look like

An app expects a filename like `report.pdf` and builds a path like:

- allowed base: `/var/app/uploads/`
- requested file: `report.pdf`
- final path: `/var/app/uploads/report.pdf`

But if the app naively joins strings, an attacker can pass an absolute path:

- request: `/download?file=/etc/passwd`
- app does: `"/var/app/uploads/" + userInput`
- result becomes something like `/var/app/uploads//etc/passwd` (or the framework resolves it as `/etc/passwd`)
- boom: reads a sensitive file.

On Windows, the same idea includes `C:\Windows\System32\...` or UNC paths like `\\server\share\...`.

# Why it happens

Common mistakes:

- Only blocking `../` but not blocking paths that start with `/` or `C:\`
- Using path-join functions that discard the base when the second argument is absolute (many languages do this: `join("/safe/base", "/etc/passwd")` -> `"/etc/passwd"`)

# How to defend (reliably)

- Treat user input as a name, not path (use IDs or map to known filenames).
- **Allowlist** acceptable filenames (e.g. `^[a-zA-Z0-9._-]+$`).
- Resolve to a canonical path and enforce containment:
	- compute `realpath`/`resolve`
	- verify it starts with the allowed base directory
- Block absolute paths explicitly (`/`, `\`, drive letters, UNC paths).
- Don't serve files directly from sensitive locations; run with least privilege.
