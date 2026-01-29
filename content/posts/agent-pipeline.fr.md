---
title: "Agents pipeline"
date: '2026-01-29'
tags: ["prompt"]
---

Un prompt pour concevoir votre propre pipeline d’agents.

```
# Le problème

Je veux concevoir un pipeline permettant d’alimenter et d’orchestrer un ensemble d’agents.

Deux sujets principaux sont à designer :
1. **Qu’est-ce qu’un agent de code ?**
2. **Comment construire un contexte (prompt), le soumettre à l’agent et vérifier le résultat**

L’objectif global est de garder un pipeline **simple**, **observable**, et **itérable**.

# Qu’est-ce qu’un agent de code ?

Un agent de code travaille sur les repositories de mon équipe :
* repo A
* repo B
* repo C
* repo D

Caractéristiques :

* Il s’exécute **en local** sur la machine.
* Il opère via une **loop Ralph Wiggum**, avec un prompt bien défini.
  https://awesomeclaude.ai/ralph-wiggum
* Il est autonome sur son périmètre, mais doit rester **audit-able**
 et **reproductible**.

## Questions ouvertes

### Organisation des repositories

* Dans quels répertoires placer les repos ?
* Idéalement, **chaque agent dispose de ses propres copies Git** des 4 repos.
* L’agent doit pouvoir :

  * créer des branches,
  * modifier du code,
  * faire des commits,
    sans interférer avec les autres agents ou l’environnement de travail humain.

### Soumission du contexte à l’agent

* Comment fournir le contexte à l’agent ?
* Probablement via **un ensemble de fichiers**.
* Où les déposer ?
* Comment distinguer clairement :

  * le code source,
  * le contexte fourni à l’agent,
  * les artefacts produits par l’agent ?


### Fichiers de travail temporaires
* Lorsqu’un agent a besoin de créer des fichiers intermédiaires :
  * où doivent-ils vivre ?
* Contraintes :
  * ne pas polluer les repos Git,
  * ne pas mélanger avec le contexte,
  * être clairement rattachés à **une exécution précise**.

### Restitution

* À la fin de son exécution, l’agent doit être capable de produire :
  * un **rapport synthétique** de ce qu’il a fait,
  * les décisions prises,
  * les changements effectués,
  * les points bloquants éventuels.

# Construire un contexte, le soumettre, et vérifier le résultat

À chaque fois qu’un agent est sollicité, on lui soumet un **prompt**.
Ce prompt est construit à partir d’un **contexte**.
Ce contexte lui-même est composé d’un **ensemble de fichiers**.

La question clé devient donc : Comment organiser ces fichiers de contexte ?

## Vers une unité de travail explicite

Chaque *prompt / contexte / tâche* (le nom reste à définir)
pourrait être matérialisé par :

* **un répertoire dédié**, fourni à l’agent au lancement,
* contenant :
  * les fichiers de contexte,
  * éventuellement des règles ou contraintes,
  * et servant de point d’entrée unique.

À la fin de l’exécution :

* l’agent écrit ses résultats **dans ce même répertoire** :
  * rapport,
  * logs,
  * décisions,
  * liens vers commits ou branches créées.

## Organisation globale

* Tous ces répertoires de tâches seraient stockés **au même endroit**.
* Objectifs :
  * gestion centralisée,
  * simplicité du pipeline,
  * visibilité sur l’ensemble du travail des agents.

## Review et amélioration continue

On veut pouvoir :

* relire et reviewer ces **contextes / prompts / tâches**,
* comprendre ce qui a bien fonctionné ou non,
* identifier :
  * ce qui est prêt à être mergé,
  * ce qui nécessite des ajustements,
  * ce qui peut être réutilisé comme “pattern”.

L’enjeu n’est pas seulement l’exécution, mais la **capitalisation** :
améliorer continuellement la qualité des contextes et, par extension,
celle des résultats produits par les agents.
```

J’ai lancé ce prompt cette semaine pour me créer mon propre pipeline d’agents.
J’ai désormais un pipeline complet qui tourne en local sur ma machine, avec des agents en boucle façon *« Ralph Wiggum »*.

Mon objectif est de prendre le contrôle total de mon workflow IA, afin de pouvoir itérer, améliorer et optimiser finement la création des prompts et surtout des contextes.

Le code n’est plus le cœur de mon activité.
Aujourd’hui, mon focus s’est déplacé vers la conception des contextes : ce sont eux qui déterminent réellement la qualité, la pertinence et l’impact des résultats produits par l’IA.
