---
title: "Kata APB"
date: '2017-11-18'
---

[Admission Post Bac](https://www.admission-postbac.fr/) (APB) is the official application of the French Ministry of National Education allowing high school students to obtain enrollment in a post-secondary school or university.

The objective of this kata is to design and implement _your_ version of this application. You are free to choose your algorithm and constraints. You can be inspired by the existing application or invent your own approach.

## Problem Description

Build a program that determines the assignments of a list of students according to a list of available courses.

The program must accept as input:

- The list of students
- The list of courses

Each student and each course must be identified by a unique name. To feed your algorithm, you can add as much information as necessary to both students and courses.

The program will provide as a result a list indicating for each student the course that has been assigned to them.

## Motivations

Many katas are somewhat _artificial_. They offer interest for the algorithms they allow to implement, but have no concrete application for _real_ users. [APB](https://www.admission-postbac.fr/), on the other hand, is used by hundreds of thousands of people and has a determining impact on their lives.

Nevertheless, the subject remains quite accessible. Everyone can understand the business domain without calling on _business experts_. People young enough have themselves been confronted with APB and can remember what it can represent, and thus imagine a solution that will seem more suitable to them.

If this kata meets some success with the computer science community, it becomes possible to find different implementations, with varying levels of complexity but especially with different algorithm criteria choices. We could then compare these algorithms with each other and bring out one or more satisfactory solutions.

The original code of the first version of the application has been put online on this [git repo](https://github.com/jeantil/admission_post_bac). The bravest can try to decrypt it and perhaps improve it.

Nevertheless, the simplest probably remains to invent your own version. You can possibly be inspired by existing work, such as for example a [stable marriage](https://en.wikipedia.org/wiki/Stable_marriage_problem) algorithm.

## A Simple Solution Example

We offer you here a solution implemented in [Haskell](https://www.haskell.org/).

- There are no selection criteria for entry into courses;
- We distribute students one after the other on the list of available courses;
- The number of places per course is not limited.

You will find other simple solutions in this [git repository](https://github.com/BernardNotarianni/kata-apb).

