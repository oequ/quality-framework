# AI-Native Profile: Agent-ready

**Status:** Draft v1.5 candidate  
**Purpose:** prove that an AI SaaS product can run agentic workflows with scoped tools, validated plans, secret isolation, approvals, and safe execution boundaries.

## Required criteria

| ID | Criterion | Required result |
|----|-----------|-----------------|
| [AI9](./ai-native.md#ai9--tool-permission-scopes) | Tool permission scopes | Pass |
| [AI10](./ai-native.md#ai10--secret-isolation-and-human-approval-for-critical-actions) | Secret isolation and human approval for critical actions | Pass |

Required when workflows are generated or modified by an LLM:

| ID | Criterion | Required result |
|----|-----------|-----------------|
| [AI8](./ai-native.md#ai8--workflowspec-validation) | WorkflowSpec validation | Pass |

Required when generated or untrusted code is executed:

| ID | Criterion | Required result |
|----|-----------|-----------------|
| [AI11](./ai-native.md#ai11--sandboxed-execution-for-generated-code) | Sandboxed execution for generated code | Pass |

## Recommended criteria

| ID | Criterion | Target |
|----|-----------|--------|
| [AI12](./ai-native.md#ai12--prompt-and-model-regression-tests) | Prompt and model regression tests | Pass for business-critical prompts |
| [AI5](./ai-native.md#ai5--ai-cost-and-inference-observability) | AI cost and inference observability | Pass for complex multi-step agents |

## Evidence checklist

- Tool registry declares permission scopes and side-effect levels.
- Runtime refuses disallowed tools in restricted workflows.
- Raw secrets are never included in prompts, model messages, or tool descriptions.
- Write/destructive actions require approval or explicit pre-authorization.
- Approval logs include actor, timestamp, action, and target.
- LLM-generated workflow specs are schema-validated before execution.
- Generated code, if supported, runs in an isolated environment with resource and network controls.

## Typical failures

- Treating “the model was instructed not to do that” as an authorization boundary.
- Passing API keys or bearer tokens into system prompts.
- Allowing agents to call write tools without approval.
- Executing generated Python/Node code on the application host.
- Running dynamic workflows without schema validation or bounded execution.

## Non-goals

- This profile does not require a visual workflow canvas.
- This profile does not require generic no-code automation features.
- This profile measures runtime safety, not workflow-builder UX.

## Related criteria

- [S8 — No dynamic code execution](../rubric/05-security.md)
- [S9 — Guards are UX only](../rubric/05-security.md)
- [A6 — Acyclic dependencies](../rubric/01-architecture.md)
- [T11 — Adapter contract tests](../rubric/04-testing-ci.md)

