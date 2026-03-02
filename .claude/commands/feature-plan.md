# /feature-plan
**Agent**: [Architect](file:///.claude/agents/architect.md)
**Skill**: [Architecture Designer](file:///.claude/skills/10-architecture/architecture-design/SKILL.md), [API Designer](file:///.claude/skills/06-api/rest-design/SKILL.md)

## Purpose
Convert an analyzed requirement into a technical blueprint, setting the state to `ARCHITECTURE_GENERATED`.

## Workflow (Surface & Adjust)
1. **Surface Requirements**: Load requirements from the Epic/RAD and verify them using [EARS](file:///.claude/skills/11-data-ml/requirement-analysis/references/ears-syntax.md).
2. **Design Data Flow**: Define DB schemas (PostgreSQL) and API contracts (OpenAPI).
3. **Draft UI/UX**: Map features to **Atomic Design** (Atoms, Molecules, Organisms).
4. **Surface Decisions**: Draft **ADRs** for non-obvious choices (e.g., Auth provider, State management).
5. **Adjust Blueprint**: Present the implementation plan to the user for feedback before setting state to `ARCHITECTURE_GENERATED`.

## Output
- `docs/features/{feature_name}_design.md`
- New ADR entries in `docs/architecture/adr/`.
