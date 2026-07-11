# Christophe Pennetier

## I build environments where intelligence has to earn its cost.

The interesting question is not whether a system can produce a plausible answer. It is whether a more expensive form of reasoning—search, learning, optimization, or human judgment—changes the decision enough to justify being used.

My work makes that question measurable.

**Proposal mechanisms may be heuristic or learned. Feasibility, execution, causality, and value are established independently of the proposer.**

This separation turns claims such as *“the model helped”* into experiments that can be reproduced, challenged, and sometimes refuted.

---

## Research program

### [Epure Arena](https://github.com/cpennetier/epure-arena)

**A certified environment for measuring decision quality under hard constraints.**

Epure evaluates policies through deterministic paired worlds, exact counterfactual pricing, eval-blind protocols, typed failure attribution, and regret against certified references.

Its current study, the **Coordination Frontier**, asks where richer proposal mechanisms create measurable value—and where a cheaper rule, search procedure, or verifier is already sufficient.

**This is the flagship repository. Start here.**

---

### [Ephemeris Kernel](https://github.com/cpennetier/ephemeris-kernel)

**A deterministic time-and-truth runtime for agentic environments.**

Ephemeris provides total event order, deterministic replay, append-only causal ledgers, explicit capacity state, byte-identical snapshots, and cryptographic run manifests.

Its purpose is simple: identical worlds and identical actions should produce identical evidence.

Ephemeris contains no policy, optimizer, or domain logic. It provides the neutral execution substrate on which decisions can be evaluated without simulator drift.

**Rust core. Python interface.**

---

### [Spectral Graph PatternBoost](https://github.com/cpennetier/spectral-graph-patternboost)

**Search-based proposal generation for constrained graph structures.**

This repository studies how to construct sparse, geometrically feasible graphs with strong algebraic connectivity.

It combines an exact spectral objective, population-based pattern search, a learned surrogate, and strong classical baselines. The experiments also document where simulated annealing remains better than the learned-search approach at the tested scale.

The negative result is part of the contribution: a more elaborate mechanism should not receive credit when a cheaper one performs better.

---

### [Spectral Graph Diffusion](https://github.com/cpennetier/spectral-graph-diffusion)

**Learned proposal generation for graphs with prescribed global structure.**

This repository implements discrete denoising diffusion for graph generation conditioned on algebraic connectivity.

The system includes a JAX/Flax graph model, deterministic data generation, an exact Rust spectral verifier, classifier-free guidance, and diagnostics separating genuine structural control from simpler changes in graph density.

The central finding is not merely that conditioning works. It is that its behavior changes across identifiable spectral regimes, with clear limits near and beyond the support of the training distribution.

---

## One research contract, two experimental tracks

These repositories are not one software stack. They are four experimental instruments built around the same contract:

```text
        PROPOSAL                         INDEPENDENT TRUTH

  heuristic search  ───────┐
  learned generation ──────┼──▶ exact structural verification
  rules and policies ──────┼──▶ deterministic execution
  optimization ────────────┘    certified decision evaluation
```

The spectral repositories hold the problem fixed while changing the proposal mechanism:

```text
constrained graph design
        ├── search-based proposals
        └── learned proposals
                 ↓
        exact spectral measurement
```

Ephemeris and Epure do the same for sequential decisions:

```text
policy proposal
        ↓
deterministic world execution
        ↓
counterfactual reconstruction
        ↓
certified value and regret
```

The shared question is:

> **For this problem, what kind of intelligence was actually necessary?**

---

## Current frontier

The next question is prospective.

It is useful to discover *after an experiment* that a sophisticated method was unnecessary. It is more valuable to predict that *before paying for it*.

**Vigie** is the prospective regime-diagnosis layer: given inexpensive observable features, predict the cheapest decision mode likely to be sufficient.

**Cénacle** is the broader agentic architecture: diagnose the regime first, allocate an appropriate reasoning budget, generate candidate decisions, and retain independent verification as the final authority.

```text
observe
   ↓
diagnose the regime
   ↓
select the cheapest sufficient reasoning mode
   ↓
propose
   ↓
verify
   ↓
act
```

---

## Background

I am a research scientist and systems builder with a PhD in operations research.

My work spans deterministic simulation, reinforcement learning, multi-agent systems, structured generation, optimization, and decision evaluation. I care about systems whose claims survive exact measurement—and about results that state clearly both what they establish and what they refute.

> **Build the world first. Let intelligence compete inside it. Measure what it actually changed.**
