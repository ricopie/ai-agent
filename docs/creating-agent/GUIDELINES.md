# Agent Creation Guidelines

## ✅ Dos

### Domain Design
- ✅ Define ONE clear specialization per agent
- ✅ Document exact boundaries (what it does NOT do)
- ✅ Specify which agents it collaborates with
- ✅ Create reusable prompts that don't need per-task customization

### Prompt Engineering
- ✅ Keep prompts concise (under 500 tokens when possible)
- ✅ Use role-based language: "You are X agent responsible for Y"
- ✅ Specify exact output format (JSON, Markdown, etc.)
- ✅ Include examples for ambiguous tasks
- ✅ Define error handling behavior

### Testing & Validation
- ✅ Test with 3-5 representative inputs
- ✅ Validate that output matches specified format
- ✅ Check that agent respects its boundaries
- ✅ Ensure personality doesn't interfere with task accuracy

### Integration
- ✅ Document input/output contracts clearly
- ✅ Specify which agent calls this agent
- ✅ Define error responses
- ✅ Include timeout/fallback strategies

---

## ❌ Don'ts

### Common Mistakes
- ❌ Overlapping responsibilities with existing agents
- ❌ Over-complicated prompts with many "if-else" scenarios
- ❌ Undefined boundaries (what it can/cannot do)
- ❌ Unpredictable output formats
- ❌ Personality superseding technical accuracy

### Anti-Patterns
- ❌ Creating agent for every task (defeats the purpose)
- ❌ Making agents too generic ("helper agent")
- ❌ Long, rambling prompts that anticipate everything
- ❌ No examples of expected behavior
- ❌ Agents that modify code when they shouldn't

---

## Workflow: Adding a New Agent

### Step 1: Define the Need
**Question:** What technical specialization is missing?

Example problems:
- "We need code review expertise" → Architecture Agent
- "We need to write code" → Implementation Agent
- "We need to research packages" → Research Agent

### Step 2: Verify No Overlap

Check against existing agents:
- **Coordinator (Kato)** - Plans, delegates, reviews
- **Architecture (Utaha)** - Design, patterns, refactoring
- **Implementation (Eriri)** - Code generation, CRUD, scaffolding
- **Research (Michiru)** - Documentation, comparisons, best practices
- **QA (Izumi)** - Testing, debugging, validation

If responsibility overlaps, enhance existing agent instead.

### Step 3: Create Agent File

File location: `agents/[agent-name].md`

Use TEMPLATE.md as base. Fill in:
1. Name & Role (1 sentence)
2. 4-5 core responsibilities
3. Clear "Does Not" boundaries
4. System prompt (concise)
5. Input/Output contract
6. 2-3 examples

### Step 4: Test the Prompt

Run 3 tests:
```
Test 1: Standard case
- Input: [normal task]
- Verify: Output matches spec, task completed

Test 2: Boundary case
- Input: [task outside scope]
- Verify: Agent declines gracefully

Test 3: Error case
- Input: [malformed input]
- Verify: Clear error message
```

### Step 5: Document Integration

Update main README.md:
1. Add agent to the architecture diagram
2. Add agent to Agents section
3. Update workflow if agent changes task flow

### Step 6: Get Feedback

Submit PR with:
- Agent file
- Test results
- Updated README
- Any prompt revisions based on testing

---

## Template Checklist

Before submitting an agent:

- [ ] Agent has exactly ONE clear domain
- [ ] "Does Not" section is clear and specific
- [ ] System prompt is under 500 tokens
- [ ] Output format is specified (JSON/Markdown/Code)
- [ ] 2-3 examples provided
- [ ] Tested with sample inputs
- [ ] No overlap with existing agents
- [ ] Integration points documented
- [ ] Personality preserved without compromising quality
- [ ] README updated with new agent

---

## Examples of Good vs Bad Agents

### ✅ GOOD: Architecture Agent
```
Role: Architecture & Design Review
Responsibilities:
- Design pattern analysis
- Clean Architecture principles
- Naming conventions
- Technical decision documentation

Does Not:
- Write implementation code
- Change database schema without review
- Make product decisions
```

### ❌ BAD: Generic Helper Agent
```
Role: Helper Agent
Responsibilities:
- Do whatever the user asks
- Help with coding
- Help with design
- Help with testing
```
*(Too vague, overlaps with everything, unpredictable behavior)*

### ✅ GOOD: Research Agent Prompt
```
You are the Research Specialist. Your job is to find and
summarize official documentation.

Input: Package/framework name + topic
Output: JSON with {source_url, summary, alternatives}

Rules:
- Only official docs (no medium.com, dev.to)
- Include version info
- Cite sources

Do NOT:
- Make recommendations
- Modify code
- Make architectural decisions
```

### ❌ BAD: Research Agent Prompt
```
You are helpful research assistant. You can research anything,
find solutions, explain concepts, and also maybe help with
code if needed. Be creative and helpful.
```
*(Vague, allows overlap, unpredictable)*

---

## Evolution Philosophy

From README:
> "Rather than anticipating every possible scenario, each agent focuses on a clearly defined responsibility. Additional instructions are introduced only when real-world usage demonstrates a need."

This means:
1. **Start minimal** - Prompt is simple and focused
2. **Collect feedback** - See where agent struggles
3. **Iterate small** - Add specific rules only when needed
4. **Avoid bloat** - Don't preemptively add "what if" scenarios

Keep prompts maintainable and evolving, not static and over-engineered.
