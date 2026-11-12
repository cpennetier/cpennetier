# PRD: what and why

Status: describes the profile at commit `81f60ab` (11 Jul 2026). Owner: Christophe Pennetier. Written 11 Nov 2026, after the fact; no earlier PRD existed.

## Problem and why now

A visitor to the GitHub profile meets four public repositories with nothing saying how they relate. `README.md` answers that in one page: one research question, one contract that keeps proposal apart from verification, and the four repositories that test it.

Why now: the profile has not changed since 11 Jul 2026 (`git log`). Its flagship, Epure Arena, published its first study as tag `v0.2.0` that same day and has had commits since, the latest on 4 Nov 2026 (GitHub API, read 11 Nov 2026). The profile calls that study current but does not link it.

## For whom

Readers of `https://github.com/cpennetier`. The job: grasp the research program in one page, then reach the right repository, flagship first (`README.md` line 25). The repository does not say who these readers are.

## Goals and non-goals

Goals: state the research question and its contract; route readers to the four public repositories; keep the negative results visible.

Non-goals: an application, a site or a build; hosting results, papers or data, which live in the linked repositories; listing work that is not public.

## What success looks like

| Measure | Threshold | How measured | Value, 11 Nov 2026 |
|---|---|---|---|
| Repository links resolving to a public repository | 4 of 4 | `gh repo view` on each link | 4 of 4 |
| `README.md` present and not empty | true | the push check (EDD, Tests) | true |
| Simulated annealing negative result stated | at least 1 line | `grep -i annealing README.md` | 1 line (line 49) |
| Claims matching the linked repository's README | every claim | read both side by side | not yet checked |

## The goal it serves

The research program in the README's first heading: environments where intelligence has to earn its cost, with every proposal mechanism judged by independent verification.

## Where its result goes

The live GitHub profile page, `https://github.com/cpennetier`. GitHub renders this repository's `README.md` from `main` there, so a push publishes it. Commit `81f60ab` adds only one blank line, to force a re-render.

## Requirements

Must:
- M1. `README.md` exists and is not empty. Test: the push check.
- M2. Every repository link resolves to a public repository. Test: `gh repo view` per link, before any push that touches links.
- M3. The negative results stay stated, not softened. Test: the annealing grep above; diff review.
- M4. Every claim, number and date traces to the owner or to the linked repository's README. Test: diff review against those READMEs.
- M5. Nothing private: no private repository, person, local path or secret. Test: diff review.

Should:
- S1. The Epure Arena entry links the published Coordination Frontier note and its reproduction steps. Test: the link resolves. Roadmap R1.

Could:
- C1. Vigie and Cénacle link to public work once it exists. Roadmap R2, parked.

## Open questions for the owner

1. Who is the intended reader: researchers, reviewers, collaborators, hiring teams? It changes what success means.
2. Is a length ceiling wanted? The README is 683 words today (`wc -w`, 11 Nov 2026).
3. Should Vigie and Cénacle stay unlinked until public, or be marked as not yet public?
