---
name: monetize-marketing
description: "Use when the user mentions Monetize Marketing, their mission, their Brain, their membership training, prompts, skills, routines, Library or Shop Builder, or asks what to work on next. Requires the Monetize Marketing MCP (https://app.monetizemarketing.com/api/mcp) connected and signed in."
license: MIT
metadata:
  author: monetizemarketing
  version: "1.0.0"
  homepage: https://github.com/monetizemarketing/skills
---

# Monetize Marketing

The Monetize Marketing MCP exposes the member's own data: their Brain (saved facts), their mission (90-day goal + goals), training transcripts, the prompt library, saved skills and routines, the Library (documents + files) and, on Platinum, the Shop Builder. Every tool runs with the member's own tier gates and credit meter. Use the tools in this order.

## 1. Orient before you act

1. `memory_get_profile` — who they are, niche, core offer, 90-day goal.
2. `get_mission` — the live mission and which goals are open.
3. `memory_search` with the task's nouns — decisions and facts already saved. Never ask the member for something the Brain already knows.

## 2. Research with their training first

- `search_course_transcripts` before any outside search: the answer is often in a lesson they paid for.
- `search_prompt_library` + `get_prompt` for a ready prompt; `get_brand_voice` before writing anything in their voice.
- `web_search` / `web_read` / `get_ai_news` only after that (Gold and up; the tool list tells you what the key allows).

## 3. Build, then save

- A reusable procedure → `run_skill` / `run_catalog_skill`; a recurring one → `create_routine` (confirm the schedule with the member first).
- A finished deliverable → `save_document` so it lands in Library → Documents. Say the document title back.
- A new durable fact (a decision, a number, a person) → `memory_save` with the right `kind`. Ask before saving anything the member did not state.

## 4. Close the loop

- A goal done → `update_goal_status` with the goal id from `get_mission`.
- Credits are real money: check `get_credit_balance` before `generate_image` / `generate_video`, and tell the member the cost first.

## Rules

- Tools are refused outside the member's tier or key scope ("This Brain key is not allowed to use that tool."): say which tool, do not retry, do not work around it.
- Never store secrets in the Brain. Never save another person's private data.
- Dates in the Brain are absolute (ISO); write them that way.
- When the connector is not connected, send the member to https://github.com/monetizemarketing/mcp and stop.
