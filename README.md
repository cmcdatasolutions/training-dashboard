# Training & Development Dashboard

Web version of the Power BI *Training & Development* dashboard, hosted on GitHub Pages.

**Link to share:** https://cmcdatasolutions.github.io/training-dashboard/

## How access works
- Everyone signs in with their **email address and password**.
- Each user's data is stored **encrypted with their own password** (AES-256, PBKDF2 310,000 rounds) in `data/u/`.
  The files in this public repo can't be read without the password.
- A viewer's file contains **only the rows they are allowed to see**, so limits can't be bypassed.
- **Admins** see all data and get an **Admin** button to manage users and publish.

## Permissions (per user)
| Setting | Meaning |
|---|---|
| Locations | Only these location codes (empty = all) |
| Programs | IAP-2023, IAP-2024, IAP-2025, Nursing Orientation |
| Module titles | Specific modules |

A row is shown when its location is allowed **and** it matches a selected program **or** a selected module (empty lists = no limit).

## Admin tasks (all in the browser)
1. **Add / edit / remove users**: Admin → *Users & permissions*. Use **Generate** for a password and send it to the user privately.
2. **Refresh the data**: Admin → *Data* → load the new `Dashboard_Data` Excel/CSV export (same column headers).
3. **Publish**: Admin → *Publish*. Needs a GitHub fine-grained token:
   github.com → Settings → Developer settings → Fine-grained tokens → *Only select repositories: training-dashboard* →
   *Repository permissions → Contents: Read and write*.
   Users see changes on their next sign-in or page refresh.

Nothing is saved until you click **Publish**.

## Notes
- Passwords can't be recovered. If a user forgets theirs, an admin sets a new one and publishes.
- Removing a user deletes their data file on the next publish. (Old versions remain in git history, but they are
  encrypted with that user's old password and only contain what they could already see.)
- The Program Title groups come from the original Power BI `MODULE_SELECT` column (`PROGRAM_MAP` in `index.html`).
