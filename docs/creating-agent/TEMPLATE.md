# Agent Creation Template

Guide lengkap untuk membuat agent baru dalam sistem multi-agent ini.

## Struktur Dasar

Setiap agent harus mendefinisikan:

### 1. **Identity & Role**
```
🔤 Agent Name
Role: [Primary Responsibility]
Personality: [Brief trait]
```

### 2. **Core Responsibilities**
Daftarkan tugas-tugas spesifik yang menjadi expertise agent:
- Task 1
- Task 2
- Task 3

### 3. **Boundaries (Does Not)**
Jelas-jelas tentukan apa yang **bukan** tanggung jawab agent:
- ❌ Redesign architecture (jika bukan Architecture Agent)
- ❌ Modify project code (jika bukan Implementation Agent)
- ❌ Make product decisions (jika bukan Coordinator)

### 4. **System Prompt**
Prompt yang konkret dan actionable:

```markdown
You are [Agent Name], responsible for [specific domain].

Your expertise:
- [Expertise 1]
- [Expertise 2]
- [Expertise 3]

When given a task:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Output format:
- [Format requirement]
- [Format requirement]

Boundaries:
- Do NOT [boundary 1]
- Do NOT [boundary 2]
```

### 5. **Input/Output Contract**

**Input Expected:**
- Type: [string/json/code]
- Example: [example input]

**Output Format:**
```
[Expected output structure]
```

### 6. **Examples**

Provide 2-3 concrete examples:

**Example 1: [Scenario]**
- Input: `[input]`
- Expected Output: `[output]`

---

## Template untuk Agent Baru

```markdown
# 🔤 [Agent Name]

## Role
[Single sentence describing primary function]

## Specialization
[Technical domain expertise]

## Core Responsibilities
* [Task 1]
* [Task 2]
* [Task 3]
* [Task 4]

## Does Not
* ❌ [Out of scope 1]
* ❌ [Out of scope 2]

## System Prompt

```
You are [Agent Name]. Your responsibility is [main task].

Your domain:
- [Domain area 1]
- [Domain area 2]

Guidelines:
1. [Guideline 1]
2. [Guideline 2]
3. [Guideline 3]

Always:
- [Requirement 1]
- [Requirement 2]

Never:
- [Boundary 1]
- [Boundary 2]

Output as:
[Format specification]
```

## Input/Output

**Input:** [Description]
**Output:** [Description]

## Integration Notes

- Called by: [Which agent(s) call this]
- Returns to: [Coordinator or specific agent]
- Dependencies: [Any other agents]

## Examples

### Example 1
**Input:** `[sample input]`
**Output:** `[sample output]`

```
```

---

## Design Principles

1. **Clear Scope** - Each agent has exactly one domain
2. **No Overlap** - Responsibilities don't conflict with other agents
3. **Maintainability** - Prompts are concise and focused
4. **Personality Over Substance** - Character flavor doesn't compromise quality
5. **Testability** - Output format is predictable and parseable
