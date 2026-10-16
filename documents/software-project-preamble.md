---
type: document
id: software-project-preamble
title: "Software Project — Starting Shape"
description: "The starting shape of a software project: what each installed pipeline is for, and when to reach for it"
tags: [Production, Template]
connections: []
metadata:
  template_category: "Project Types"
---

## Software Project

This project starts with the pipelines software work repeats, in the order the work tends to arrive: specify, review, audit, document. Nothing here is prescriptive — remove what your team does not use.

### What is installed, and when to reach for it

**Feature Spec Pipeline** — before code. Turns a rough intent into a specification with scope, acceptance criteria and the questions still open. Reach for it when a request arrives as a sentence and has to become something a developer can build against.

**Code Review Pipeline** — on a change. Reviews a diff for correctness, security and style, producing inline comments and an approval decision. It runs *before* a human read, not instead of one.

**Security Audit Pipeline** — on a component, or before a release. Looks for vulnerabilities and insecure patterns. Optional: many teams run security on their own cadence rather than per change.

**Documentation Pipeline** — after a change settles. Produces documentation from the code and the decisions behind it. Optional.

### The order they tend to run in

```
feature-spec  ->  (build)  ->  code-review  ->  security-audit
                                     |
                                     +-------->  documentation
```

That is a tendency, not a dependency. Each pipeline runs on its own, and none requires another's output.

### What is deliberately not here

**No test pipeline — yet.** Testing belongs in this shape and a stage for it is coming. Until one is ready to earn its place, this template leaves it out rather than including something that would not do the job.

### What this project does not assume

- **No repository is connected.** Every pipeline works on content you paste or point it at.
- **No issue tracker, no CI.** Nothing here reaches outside the app.
- **No house style.** The pipelines that care about tone read a style source you supply; until you provide one they use a neutral professional default.

### Making it yours

The most useful first change is to give review and documentation your own conventions — a style source for writing, and your own severity definitions for triage. Both are ordinary content you author in the app; neither needs a pipeline edited.

If a pipeline here does not fit how you work, remove it. A project carrying a pipeline nobody runs is harder to understand than one carrying two.
