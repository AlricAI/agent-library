# Rete Overview

> Epona is a greenfield implementation of the RETE algorithm in Elixir.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Epona — A RETE Engine for Elixir

Epona is a greenfield implementation of the RETE algorithm in Elixir. RETE is an efficient, incremental pattern-matching algorithm for production rule systems (expert systems, CEP engines, business rules). This overview introduces RETE, its core parts (Alpha and Beta networks), and outlines concepts that guide the design of this project.

## What Is RETE?

RETE (by Charles Forgy) accelerates rule evaluation when you have many rules operating over a changing set of facts (working memory). Instead of re-scanning all rules against all facts after each change, RETE:

- Caches intermediate matches in a graph of nodes.
- Shares common condition tests across rules.
- Propagates only incremental changes (assert, modify, retract).
This transforms repeated global searches into localized updates, trading extra memory for much faster matching in dynamic environments.

## Core Concepts

- Working Memory Elements (WMEs): Structured facts asserted into the engine (e.g., maps or structs). They have attributes/fields used in conditions.
- Rules (Productions): If-then statements with a left-hand side (LHS) of conditions/patterns and a right-hand side (RHS) of actions to fire when conditions are satisfied.
- Rete Network: A directed graph that matches facts against rule conditions. It consists of the Alpha network (single-fact tests) feeding the Beta network (joins across multiple facts) and ends at production nodes.
- Activations & Agenda: When a rule’s LHS is satisfied, an activation is placed on an agenda. A conflict resolution strategy selects which activation to fire next.
- Refraction: A policy to prevent a rule from firing repeatedly on the exact same combination of facts unless those facts change.

## The Rete Network at a Glance

The network is built from rule conditions and shared across all rules:

- Nodes: Test nodes, memories, join nodes, and production nodes form a DAG-like structure rooted at the top.
- Direction: Facts flow downward 

*[truncated — see source for full prompt]*