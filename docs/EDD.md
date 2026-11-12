# EDD: how it is built

## Context and scope

The repository is the owner's public GitHub profile. Its product is `README.md`, which GitHub renders at `https://github.com/cpennetier`. This document covers the README's structure, how a change reaches the page, and how it is checked and undone. The four linked repositories are out of scope.

## Design

One file. No code, no dependencies, no build, no CI: there is no `.github/` directory (11 Nov 2026).

The README is a route for the reader (`grep '^#' README.md`):

1. Thesis: the first heading and the split between proposal and verification.
2. Research program: one section per public repository, flagship first.
3. One research contract, two experimental tracks: ASCII diagrams in `text` code fences, which render the same on every screen.
4. Current frontier: Vigie and Cénacle, named without links.
5. Background.

Data flow: an edit is committed on `main`, the push check runs locally, the push publishes, and GitHub re-renders the page. Reused: GitHub's Markdown renderer and profile README feature, nothing else.

## Alternatives considered

None is recorded. The history holds two commits, both on 11 Jul 2026, and no document existed before these.

## Tests

- Small (under 1 s, no I/O): none. There is no code.
- Medium (under 30 s, local I/O): the push check. It asserts that `README.md` exists, is not empty and carries no stray machine-written header. It runs before every push and took 0.00 s real on 11 Nov 2026. It proves presence, not quality.
- Large (network): the link check, `gh repo view` on each of the four links; all four were public on 11 Nov 2026. Manual, before any push that touches links. After a push, a look at the rendered page.

No test proves that claims match the linked repositories or that the negative results are intact. Diff review does, before each push (PRD, M3 and M4).

## Security, privacy and observability

- Public repository: every tracked line is world-readable once pushed. No secret, key, local path or private person belongs here.
- Tracked files: `README.md` and, from this commit, `docs/` (`git ls-files`).
- Observability: the Git history and the rendered page. No analytics, no logs.

## Cost

- Money: zero. No CI, no deploy, no paid service, no dependency.
- Compute: none at run time; the push check takes under 0.01 s.
- Tokens and time: one short editing session per change. Not measured.

## Risks, rollout and the way back

| Risk | Effect | Mitigation |
|---|---|---|
| A push publishes at once | an error is public immediately | read the full diff before pushing |
| A linked repository is renamed, made private or deleted | a broken link | the link check before pushes that touch links |
| Claims drift from the linked repositories | the page overstates or understates | compare with the linked READMEs when they change (roadmap R1) |
| GitHub shows a stale render | the old page stays visible | a one-line commit forced a re-render once (`81f60ab`) |

Rollout: a push to `main` is the release; there is no staging. The way back: `git revert <sha>`, then push; GitHub re-renders from the reverted file.

## Open questions

1. Should the link check join the push check? It needs the network, which turns a local check into a large one.
2. Should these documents live in the public repository at all, given that the profile shows only the README?
