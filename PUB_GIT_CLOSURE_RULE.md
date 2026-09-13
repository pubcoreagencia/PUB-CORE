# PUB Git Stage Closure Rule

**Effective:** 2026-09-13
**Scope:** This repository
**Status:** Mandatory operational rule

## Rule

A development stage may be declared **CLOSED / COMPLETE / PASS** only when all of the following are true:

1. The implementation is complete.
2. Required tests and validation gates pass.
3. The working tree is clean.
4. All intended changes are committed.
5. The commit is published to the repository's official remote.
6. Local `HEAD` is verified to match the intended remote branch state.
7. The remote state is verified after publication.
8. Only then may the next stage begin.

A local commit alone does **not** close a stage.

## Required closure sequence

`IMPLEMENT → TEST → COMMIT → PUSH → VERIFY REMOTE → DECLARE CLOSED → NEXT STAGE`

## Exception

If publication is intentionally withheld for security, review, or another explicit reason, the stage must be recorded as:

**IMPLEMENTED LOCALLY / NOT YET PUBLISHED**

It must not be described as CLOSED or COMPLETE.

## Pre-next-stage gate

Before starting a new stage, verify the previous stage's remote commit and confirm that GitHub reflects the state declared complete.

## Source of truth

For repository state, GitHub is the source of truth. Local state is provisional until synchronized and verified remotely.
