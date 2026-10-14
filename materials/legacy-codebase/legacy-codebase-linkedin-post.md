# LinkedIn Post: AI-Native Work in Legacy Codebases

Most AI coding advice assumes a greenfield project.

But the hard work happens in legacy codebases: the systems with years of business rules, invisible contracts, stale documentation, and a test suite that is both your safety net and your map.

The AI-native answer is not “put the whole repository into the prompt.”

It is to give the agent a **context harness**.

Here is the workflow I use for brownfield work:

1. **Map the smallest safe change surface**
   Start with repository instructions and AI policies. Then trace one path from the entry point to the state change and the nearest test. The objective is not a beautiful repository summary; it is evidence for one requested behaviour.

2. **Make the change radius explicit**
   Name the code and behaviour that may change — and what may not. For example: “fix this validation path and its nearest tests; do not change the public API, dependencies, or adjacent rules.” A declared radius keeps an agent from turning a bug fix into speculative refactoring.

3. **Separate investigation from implementation**
   First ask for a map: relevant files, evidence, risks, validation commands, and open questions. Approve the plan. Only then let the agent edit. This simple gate removes a surprising amount of confident guessing.

4. **Use project memory, not chat history**
   Save verified facts in a compact file: repository revision, local rules, execution paths, test commands, decisions, risks, and unresolved questions. Memory is not a transcript. It is a durable handoff so the next session starts with evidence instead of rediscovery.

5. **Prove a narrow change**
   Add focused regression coverage, run the closest relevant checks, review the diff, and record residual risk. Expand testing when policy or dependency risk calls for it — not by reflex.

The loop is simple:

**investigate → map → approve → change → validate → remember**

AI becomes useful in a legacy system when it helps the team reduce uncertainty, not when it merely produces code quickly.

What is the one thing your agents most often miss when they enter an unfamiliar repository: hidden rules, test seams, architectural boundaries, or institutional memory?

#AIEngineering #LegacyCode #SoftwareArchitecture #AICoding #AgenticAI #DeveloperExperience
