# ERD: what the engine or data must provide

There is no engine and no data. The repository holds one Markdown file, `README.md`, which GitHub renders as the profile page. Nothing runs, nothing is stored, nothing is fetched. This document records that, and the few guarantees the file still needs.

## Inputs and outputs

- Input: `README.md`, GitHub-flavored Markdown: 141 lines, 683 words, 5,592 bytes (`wc`, 11 Nov 2026).
- Output: the rendered profile at `https://github.com/cpennetier`. GitHub produces it; this repository does not.
- Schema: none. The only external references are four links to public repositories (`README.md` lines 17, 29, 43 and 55).

## Guarantees

| Guarantee | Held by |
|---|---|
| `README.md` exists and is not empty | the push check (EDD, Tests) |
| Every repository link resolves to a public repository | a manual `gh repo view` on each link; no automated test |
| The negative results stay stated | diff review, and `grep -i annealing README.md` |
| Nothing private is tracked | `git ls-files` lists only public documents; diff review |

No guarantee is held by a test file: the repository has none. Determinism does not apply, since nothing is computed.

## Data

None. All content is public text written by the owner. Retention: the Git history, here and on GitHub, kept indefinitely. Nothing private is collected or stored.

## Budgets

No latency, memory or money budget applies, because nothing runs. The push check completes in under 0.01 s (`time -p` reported 0.00 s real, 11 Nov 2026).

## Failure

- A linked repository is renamed, made private or deleted: its link breaks silently. Only the manual link check finds it; nothing alerts.
- GitHub shows a stale render: the history records the fix used once, commit `81f60ab`, which added one blank line to force a re-render.
- A wrong push: it is public at once. The way back is a revert (EDD, Risks).
