# Architecture

This document defines the high-level architecture for Echo AI.

## Goals
- Modular, testable components
- Clear data boundaries and privacy controls
- Human-in-the-loop review for all outputs

## Core Components
- data/: schemas and synthetic samples only
- prompts/: prompt templates and guardrails
- training/: preprocessing and evaluation pipelines
- models/: model references and configs (no weights)
- api/: LLM clients, moderation, and policy enforcement
- app_integration/: app-facing payloads and integration adapters

## Data Flow (High Level)
1. App sends structured request payloads to the API layer.
2. API validates payloads against schemas.
3. Prompt layer builds context and applies guardrails.
4. Model client generates a draft response.
5. Moderation and policy checks run.
6. Human review confirms or edits before final output.

## Boundaries
- No real patient data in this repository.
- Audio and raw sensitive inputs are never stored.
- Final responsibility remains with licensed professionals.
