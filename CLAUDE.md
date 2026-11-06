# llevintza/llevintza — public profile repo

This repo's `README.md` renders on the public GitHub profile page. Treat everything in it as visible to recruiters, employers, and the public internet.

Full background/career data lives in a separate **private** sibling repo (`resume-data`). This repo should only ever contain the short, polished "elevator pitch" version.

## Before editing README.md

Never add any of the following here, even paraphrased:

- Full home address or precise location finer than city
- Phone number
- Personal email, if a contact-form or alternative exists
- Salary, compensation, equity, or offer details — past or present
- Employer-confidential project names, internal codenames, or proprietary metrics not publicly disclosed by the employer
- Specific client/customer names under NDA
- Performance review content, manager names, or internal org-chart details
- Anything tagged `visibility: private` in the `resume-data` repo's frontmatter

If unsure whether something is safe to include, leave it out and add it to `resume-data` instead with the appropriate `visibility` flag.

## Building section rules

The `## Building` table is the only list of projects. Re-audit it whenever projects change:
`gh repo list llevintza --limit 200 --json name,visibility,isFork,pushedAt,description`

- **Eligible:** your own work (not a fork), with a README that says what it is and real code beyond a scaffold (not README-only or a single commit). It must not be interview/exam prep, personal infra or dotfiles, a prompt/persona store, or client work. A finished private build shared on request is allowed when it works as a standalone product and nothing a grantee can see names a third party. Prep repos (drills, practice scaffolds, design-only defenses) stay excluded.
- **Public repo:** the name is a link.
- **Private repo:** allowed only as plain text `name (private)` with **no link**, because a private link 404s for visitors. Its Access cell is `On request`, or the Request access badge once the repo passes the pre-share checks (kept in `resume-data`). It's better to make the repo public and then link it. Before a repo goes public, scan its HEAD *and* history (including `.mailmap`, docs and commit emails) for employer/client names and secrets.
- **Description:** one sentence on what it is, plus its maturity (`Phase N`, `vX.Y.Z`, `Early MVP`). No employer or client names, no "interview" framing, no "rebuild of what I did at X".
- **Row format:** `| [name](url) | description | up to 6 stack items joined by " · " | access |`, where access is `Public`, `On request`, or the mailto Request access badge. The badge links to a `mailto:`, never to the private repo.
- **Live site:** if a project has a public site, add `<br>[Live site](url)` after the name in the Repo cell; otherwise add nothing. A private repo's row may link its live site, just not the repo. Only list a site that loads and whose API responds, and update the link whenever the site moves. Audit with `gh api repos/<owner>/<repo>/pages`.
- **Order:** most recently pushed first. **Cap:** 10 rows; when over the cap, drop the least recent or least substantive row.
- Deliberately excluded: `grok-bots` (persona store), `regent`, `instrument-price-dashboard-client` (duplicate), `ticker-lens`, `market-data-platform`, `data-stack-labs`, interview/exam repos, and design-only assignment repos. Never name a repo here whose name embeds a company.

## Access requests

- Intake is by email only. Never use public issues, because they would show who is reviewing the code.
- Shared private repos live in a single organization, so access can be read-only. Collaborators on a personal-account repo always get write access.
- Grant read-only access per repo and per person: `gh api -X PUT repos/<org>/<repo>/collaborators/<user> -f permission=pull`. Invites expire after 7 days. Revoke with `-X DELETE` when the review is over. Never grant write.

## Style

- Keep it short — this is a profile page, not a resume. Hand-edit prose directly; no generator/build step.
- Prefer GitHub-native features (pinned repos, badges) over hand-maintained content where possible.
