# /epic-start
**Agent**: [Requirement Analyzer](file:///.claude/agents/requirement-analyzer.md) 
**Skill**: [Feature Forge](file:///.claude/skills/11-data-ml/requirement-analysis/SKILL.md)

## Purpose
Initiate a high-level goal (Epic), set the project lifecycle state to `ANALYZING`, and surface potential architectural risks.

## Workflow (Surface & Adjust)
1. **Surface Vision**: Interview the user to extract the "Why", "Who", and "What" of the epic. 
2. **Steelmann Requirements**: Restate the objectives in their strongest form using the [Requirement Analyzer](file:///.claude/agents/requirement-analyzer.md).
3. **Analyze Risk**: Score dimensions (1-100) for `COMPLEXITY`, `SCALABILITY`, and `SECURITY`.
4. **Define Success**: Establish concrete North Star metrics for the epic.
5. **Adjust & Set State**: Finalize the Epic Definition Document (EDD) and set global state to `ANALYZED` in `CLAUDE.md`.

## Output
- `docs/epics/{epic_name}.md` (The Source of Truth)
- Updated `CLAUDE.md` lifecycle status.
