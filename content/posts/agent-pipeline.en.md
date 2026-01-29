---
title: "Agent Pipeline"
date: '2026-01-29'
tags: ["prompt"]
---

A prompt to design your own agent pipeline.

```
# The Problem

I want to design a pipeline to feed and orchestrate a set of agents.

Two main topics to design:
1. **What is a code agent?**
2. **How to build a context (prompt), submit it to the agent, and verify the result**

The overall goal is to keep a pipeline that is **simple**, **observable**, and **iterable**.

# What is a code agent?

A code agent works on my team's repositories:
* repo A
* repo B
* repo C
* repo D

Characteristics:

* It runs **locally** on the machine.
* It operates via a **Ralph Wiggum loop**, with a well-defined prompt.
  https://awesomeclaude.ai/ralph-wiggum
* It is autonomous within its scope, but must remain **auditable**
  and **reproducible**.

## Open Questions

### Repository Organization

* In which directories should we place the repos?
* Ideally, **each agent has its own Git copies** of the 4 repos.
* The agent must be able to:

  * create branches,
  * modify code,
  * make commits,
    without interfering with other agents or the human work environment.

### Submitting Context to the Agent

* How to provide context to the agent?
* Probably via **a set of files**.
* Where to place them?
* How to clearly distinguish:

  * the source code,
  * the context provided to the agent,
  * the artifacts produced by the agent?


### Temporary Working Files
* When an agent needs to create intermediate files:
  * where should they live?
* Constraints:
  * don't pollute Git repos,
  * don't mix with context,
  * be clearly tied to **a specific execution**.

### Output

* At the end of its execution, the agent must be able to produce:
  * a **summary report** of what it did,
  * decisions made,
  * changes performed,
  * any blocking points.

# Building a Context, Submitting It, and Verifying the Result

Each time an agent is invoked, we submit a **prompt** to it.
This prompt is built from a **context**.
This context itself is composed of a **set of files**.

The key question therefore becomes: How to organize these context files?

## Towards an Explicit Work Unit

Each *prompt / context / task* (the name remains to be defined)
could be materialized by:

* **a dedicated directory**, provided to the agent at launch,
* containing:
  * context files,
  * possibly rules or constraints,
  * and serving as a single entry point.

At the end of execution:

* the agent writes its results **in this same directory**:
  * report,
  * logs,
  * decisions,
  * links to commits or branches created.

## Global Organization

* All these task directories would be stored **in the same place**.
* Objectives:
  * centralized management,
  * pipeline simplicity,
  * visibility over all agent work.

## Review and Continuous Improvement

We want to be able to:

* read and review these **contexts / prompts / tasks**,
* understand what worked well or not,
* identify:
  * what is ready to be merged,
  * what needs adjustments,
  * what can be reused as a "pattern".

The challenge is not just execution, but **capitalization**:
continuously improve the quality of contexts and, by extension,
the quality of results produced by agents.
```

I launched this prompt this week to create my own agent pipeline.
I now have a complete pipeline running locally on my machine, with agents looping in *"Ralph Wiggum"* fashion.

My goal is to take full control of my AI workflow, in order to iterate, improve and finely optimize the creation of prompts and especially contexts.

Code is no longer the core of my activity.
Today, my focus has shifted to context design: they are what truly determine the quality, relevance and impact of the results produced by AI.

