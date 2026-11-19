# GLM coding and browser workflow

## Model and provider

- Use Z.AI's OpenAI-compatible Coding Plan endpoint in Cline.
- Use `glm-5.3` as the default coding model.
- Use the Z.AI Vision MCP server for image and screenshot analysis; do not send screenshots continuously.

## Browser-first UI work

- Prefer Playwright MCP accessibility snapshots and DOM inspection.
- Take a screenshot only when the DOM/accessibility information cannot answer the question or after a visible UI change needs visual verification.
- After each browser action, inspect the updated state before taking another action.
- Do not create screenshot polling loops or timer-based screen capture.

## Approval boundaries

Always ask for approval before:

- running terminal commands that modify files, dependencies, or system state;
- deleting or overwriting files;
- logging in or entering credentials;
- making payments or changing subscriptions;
- sending messages, emails, or other external communications;
- navigating to an untrusted or user-unspecified website.

Never read `.env`, `.env.*`, credential files, private keys, or password-manager exports unless the user explicitly identifies a safe, non-secret test value.

## Visual handoff

When a task includes a screenshot or image file, use the Z.AI Vision MCP tools or ask the user to provide a local image path. Return visual findings as text before making code changes.
