# Kuare CRM module updates

`manifest.json` is the list of Kuare CRM modules. Every Kuare CRM reads it once a day (Kuare Core 1.4.7+,
Kuare Core > Kuare modules) to show each module's latest version and tell administrators about updates.
A module added here appears in every CRM's list on its next check. Nothing is ever sent from a CRM: it only
downloads this file.

## Rules
- Every module release updates its entry here in the same release (`latest_version`, `released_on`,
  `min_core`, `changes`). The release agent pushes the change to `main`.
- Client-facing words only: Kuare CRM and functional module names. No vendor names, no prices, no code
  identifiers.
- Versions are `X.Y.Z` with single-digit parts. `latest_version` empty = version not followed here
  (the CRM shows installed or not installed only).
- Keep it valid JSON: a CRM that downloads a broken file keeps its last good copy.

## Fields (one object per module in `modules`)
| Field | Meaning |
|---|---|
| `key` | system name of the module (its folder) |
| `name` | name shown to clients |
| `group` | `people`, `money`, `operations`, `sales` or `tools` (see `groups`) |
| `icon` | icon name from the Kuare UI kit (unknown names show a box) |
| `description` | one sentence on what it does |
| `latest_version` | newest released version |
| `released_on` | date of that release, `YYYY-MM-DD` |
| `min_core` | lowest Kuare Core version the latest release needs (empty = none) |
| `changes` | what is new in the latest release, a few short lines |

`contact` is shown on the products page next to modules that are not installed.
