---
title: Agent Skill Generator
description: Generate a compliant Agent Skill file (SKILL.md) based on requirements description, serving as a standardized template for agent capability extension
tags:
  - skill
  - agent
  - template
  - specification
---

Generate a complete Agent Skill file (SKILL.md) based on the following requirements description. Output only the SKILL.md content, nothing else:

```
<VAR name="description" description="A one-sentence description of the skill's purpose and trigger scenarios">
  A one-sentence description of the skill's purpose and trigger scenarios
</VAR>
```

## Skill File Structure Requirements

### 1. YAML Frontmatter

- **name**: Skill name in kebab-case format
- **description**: One-sentence description of the skill's purpose and trigger scenarios

### 2. Title

- Use `#` first-level heading with the name converted to Title Case

### 3. Purpose

- Describe when this skill should be applied
- Clearly define trigger conditions and applicability boundaries

### 4. ALWAYS (Mandatory Rules)

- List mandatory rules that MUST be followed when using this skill
- Each rule should be specific and verifiable
- Use `-` list format

### 5. NEVER (Prohibited Practices)

- List actions that are FORBIDDEN when using this skill
- Include anti-patterns and common mistakes
- Use `-` list format

### 6. Common Patterns

- Provide typical usage examples
- Include code blocks where applicable
- Demonstrate correct usage and recommended patterns
- Use code blocks with language annotations

### 7. Notes

- Supplementary considerations
- Edge case handling
- Known limitations or dependencies

---

## Content Quality Requirements

### For ALWAYS Rules

- Each rule must be **atomic**, addressing only one clear constraint
- Each rule must be **verifiable** with clear pass/fail criteria
- Avoid vague language; use explicit terms like "MUST" and "MUST NOT"
- Follow the pattern established in the existing i18n Skill where applicable

### For NEVER Rules

- Each prohibition should explain **why** it is forbidden
- Provide counterexamples (marked with ❌) alongside correct code (marked with ✅)
- Cover common misuse scenarios

### For Common Patterns

- Provide at least 2-3 typical scenarios
- Examples should cover varying complexity levels
- Code examples should be runnable or easily understandable

---

## Output Format Specifications

- Output only the SKILL.md file content
- Do not output any analysis, explanation, or additional text
- Strictly follow Markdown format
- Wrap YAML frontmatter with `---`

---

## Self-Check Checklist (After Generation)

- [ ] Frontmatter contains both name and description
- [ ] First-level heading uses correct Title Case
- [ ] Purpose clearly describes application scenarios
- [ ] At least 3 ALWAYS rules, each verifiable
- [ ] At least 3 NEVER rules with example comparisons
- [ ] At least 2 Common Patterns with code blocks
- [ ] Notes include edge cases or limitations
- [ ] No output other than the SKILL.md content
