---
name: spec-generator
description: Generate comprehensive technical specification documents. Use this skill whenever the user wants to create a technical spec, design document, requirements doc, or architecture specification - whether starting from scratch or filling a template. Works for any technical domain (services, APIs, libraries, systems, etc.).
---

# Technical Specification Generator

This skill generates comprehensive technical specification documents. It supports two modes:

1. **Full Generation**: Create a complete spec from scratch based on user requirements
2. **Template Fill**: Generate/fill a spec skeleton with user-provided details

## Determining the Mode

- If the user provides detailed requirements, domain knowledge, or existing content → **Full Generation**
- If the user asks for "a template", "a skeleton", "an outline", or provides minimal info → **Template Fill**
- If unclear, ask the user which they prefer

---

## Output Format

Always output as a Markdown file (`.md`) with proper structure. Use the filename the user specifies, or default to `SPEC.md`.

---

## Full Generation Mode

When generating a complete spec, include these core sections (adapt based on the domain):

### 1. Title and Overview

```markdown
# [Project Name] Specification

Status: [Draft v1 / Review / Final]

Purpose: [1-2 sentence description of what this project/system does]
```

### 2. Problem Statement

Explain the problem being solved:
- What pain point does this address?
- Why does it need to exist now?
- What alternatives exist and why aren't they sufficient?

### 3. Goals and Non-Goals

**Goals** (what the spec WILL cover):
- Clear, measurable objectives
- What success looks like

**Non-Goals** (what's explicitly out of scope):
- Prevents scope creep
- Sets expectations

### 4. System Overview

#### 4.1 Main Components

List and briefly describe the key components:
- Component name
- Responsibility
- Key interfaces

#### 4.2 Architecture Diagram (if applicable)

Describe the architecture in text or mermaid syntax:
- Data flow
- External dependencies
- Integration points

### 5. Core Domain Model

Define the core entities:

#### Entity Name
- `field` (type): Description
- Include normalization rules if applicable

### 6. Functionality Specification

For each major feature/function:
- Preconditions
- Behavior
- Postconditions
- Error handling

### 7. Configuration Specification

Document all configurable options:
- Default values
- Required vs optional
- Environment variable overrides
- Validation rules

### 8. API/Interface Contracts

If applicable:
- Request/response formats
- Error codes
- Versioning strategy

### 9. Security and Safety

- Authentication/authorization
- Data handling
- Rate limiting
- Safety invariants

### 10. Observability

- Logging requirements
- Metrics
- Monitoring endpoints
- Debugging capabilities

### 11. Failure Model

- Failure classes
- Recovery strategies
- Degradation paths

### 12. Acceptance Criteria

Testable criteria that define when the spec is implemented correctly:
- Functional requirements
- Performance targets
- Compatibility requirements

---

## Template Fill Mode

When the user wants just a template/skeleton:

Generate a Markdown file with all section headers and placeholder comments like `[TODO: describe X]`. Include:
- All core sections listed above
- Brief guidance in italics for each section explaining what to fill in
- Example structure based on the domain if specified

---

## Writing Guidelines

1. **Be specific**: Avoid vague language. Use concrete examples.
2. **Be complete**: Don't leave important decisions undefined.
3. **Be consistent**: Use consistent terminology throughout.
4. **Be actionable**: A good spec should let a developer implement from it.
5. **Use tables**: For configurations, comparisons, and structured data.
6. **Use code blocks**: For examples, schemas, and protocol details.
7. **Number everything**: For lists that have order significance.

---

## Handling Ambiguous Requirements

If the user provides insufficient details:
1. Make reasonable assumptions and document them
2. Use placeholders like `[PROJECT_NAME]` for unclear items
3. Add `[TODO]` comments for decisions that need user input
4. Ask clarifying questions when critical information is missing

---

## Example Output Structure

```markdown
# MyProject Specification

Status: Draft v1

## 1. Problem Statement

[TODO: Explain the problem this project solves]

## 2. Goals and Non-Goals

### 2.1 Goals

- [Goal 1]
- [Goal 2]

### 2.2 Non-Goals

- [Non-goal 1]
- [Non-goal 2]

## 3. System Overview

### 3.1 Main Components

| Component | Responsibility |
|-----------|----------------|
| Component1 | Does X |
| Component2 | Does Y |

...

## 4. Core Domain Model

### 4.1 Entity: [Name]

| Field | Type | Description |
|-------|------|-------------|
| id | string | Unique identifier |
| name | string | Human-readable name |

...
```

---

## Tips for Quality Specs

- **Start with why**: Explain the motivation before the solution
- **Define terms**: Include a glossary for domain-specific terminology
- **Show trade-offs**: Document design decisions and alternatives considered
- **Be versioned**: Include status and version for tracking changes
- **Include examples**: Concrete examples clarify abstract concepts
- **Link dependencies**: Reference related specs, standards, or systems
