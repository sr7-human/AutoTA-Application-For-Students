# GLM coding setup for VS Code

This repository uses Cline in VS Code with Z.AI's GLM Coding Plan. The setup is
DOM-first for browser work and uses Z.AI Vision MCP only when visual analysis is
actually needed.

## What has already been configured

- Cline extension installed in VS Code.
- Official Playwright MCP registered with VS Code as `playwright`.
- Project rules added at `.clinerules/glm-workflow.md`.
- No API key was written to this repository or to this document.

## One-time Cline configuration

1. Open the Cline panel in VS Code.
2. Open Cline settings.
3. Choose **OpenAI Compatible** as the provider.
4. Set the base URL to:

   `https://api.z.ai/api/coding/paas/v4`

5. Enter model ID:

   `glm-5.3`

6. Paste your Z.AI API key into Cline's password/API-key field. Do not put it
   in chat, this repository, `.clinerules`, `.env`, `.zshrc`, or a shell
   command.
7. Save the provider configuration and use Cline's connection/verification
   control.

The key is entered through Cline's local settings, not a tracked file.

## Visual analysis with GLM-5.3-Flash

Add Z.AI's official Vision MCP server in Cline's MCP settings using this
configuration:

```json
{
  "mcpServers": {
    "zai-mcp-server": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@z_ai/mcp-server@latest"],
      "env": {
        "Z_AI_API_KEY": "<PASTE_LOCALLY_IN_CLINE_MCP_SETTINGS>",
        "Z_AI_MODE": "ZAI"
      }
    }
  }
}
```

Replace the placeholder only in Cline's local MCP settings. Never commit that
value. The Vision MCP provides tools such as `diagnose_error_screenshot`,
`ui_to_artifact`, `ui_diff_check`, and `image_analysis`. Give it a local image
path; do not paste a secret or private screenshot into chat.

The Vision MCP requires Node.js 22 or newer. This Mac currently has Node.js
24.10.0.

## Browser workflow

Use the already-registered Playwright MCP server for websites:

1. Navigate only to the URL you requested.
2. Prefer accessibility snapshots and DOM references.
3. Approve navigation, clicking, typing, form submission, downloads, and
   screenshots when Cline asks.
4. Take screenshots only after an action or visible change and only when
   structural inspection is insufficient.

Chrome DevTools MCP is optional and is not enabled by this setup. It grants
deep DevTools access to a browser session, so add it only for a specific
debugging need and keep its actions approval-gated.

## Safe operating defaults

- Do not enable Cline YOLO mode.
- Keep terminal execution approval-gated.
- Keep file deletion, logins, payments, subscriptions, and external messages
  approval-gated.
- Use Cline Plan mode for unfamiliar or multi-file changes, then switch to Act
  mode after reviewing the plan.
- Check `git diff` before accepting changes.

## Verification checklist

1. In Cline, verify a simple text-only request using `glm-5.3`.
2. Ask Cline to inspect a local screenshot by path through Vision MCP.
3. Ask Cline to open a harmless test page with Playwright and return its
   accessibility snapshot.
4. Confirm that navigation, clicks, typing, screenshots, and terminal commands
   still ask for approval.
5. Check the Z.AI dashboard for usage. Do not rely on the model claiming its
   own identity.

## Official references

- Z.AI Cline setup: https://docs.z.ai/scenario-example/develop-tools/cline
- Z.AI Vision MCP: https://docs.z.ai/devpack/mcp/vision-mcp-server
- GLM-5.3: https://docs.z.ai/guides/llm/glm-5.3
- GLM-5.3-Flash: https://docs.z.ai/guides/vlm/glm-5.3-flash
- Playwright MCP: https://playwright.dev/mcp/installation
- Cline approvals: https://docs.cline.bot/features/auto-approve
