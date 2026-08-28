# Publishing Upload-Post to the ChatGPT App Directory

ChatGPT Apps are built on **MCP** — the same connector that already powers these skills
(`https://mcp.upload-post.com/mcp`, OAuth). That means most of the hard work is done.
This is the checklist to go from "MCP server exists" to "listed in the ChatGPT App Directory".

## What ChatGPT Apps require

| Requirement | Status for Upload-Post | Notes |
|---|---|---|
| MCP server (the app's tools) | ✅ Live at `mcp.upload-post.com/mcp` | Required. Already exposes `upload_video`, `upload_photos`, `upload_text`, `get_analytics`, `send_dm`, scheduling, etc. |
| OAuth per-user auth | ✅ Done | Each user connects their own Upload-Post account; no API keys in prompts. |
| Identity / business verification | ⬜ To do | Verify in the OpenAI Platform Dashboard under the name you publish as ("Upload-Post" → business verification). |
| Directory metadata | ⬜ To do | Name, short + long description, category, icon, screenshots, support contact. |
| Tool annotations | ◻️ Recommended | `readOnlyHint` on reads (`get_analytics`, `list_scheduled`); `destructiveHint` on writes (`upload_*`, `cancel_scheduled`, `send_dm`). |
| UI component (iframe) | ◻️ Optional | A web component to preview the post (caption + media + target platforms) before publishing — strong differentiator. |
| Country availability | ⬜ To do | Choose markets in the submission flow. |

## Step-by-step

1. **Verify identity/business** in the OpenAI Platform Dashboard for the publishing name.
   Business verification is required to publish under "Upload-Post".
2. **Harden the MCP server for the directory:**
   - Confirm OAuth scopes are least-privilege and the consent screen names "Upload-Post".
   - Add/verify tool annotations (`readOnlyHint` / `destructiveHint`) so ChatGPT can gate
     destructive actions (publishing, DMs, cancellations) behind a confirmation.
   - Make sure each tool has a crisp, user-facing `description` (these show in ChatGPT).
3. **(Optional) Build the preview UI** — a small web component rendered in an iframe that
   shows the composed post (media thumbnail, caption, selected platforms, schedule time)
   with a Publish / Schedule button. This is what turns it from "a tool" into "an app".
4. **Test in Developer Mode** end-to-end: connect account (OAuth) → compose → preview →
   publish → poll `get_status` until `success`.
5. **Prepare directory metadata:**
   - Name: `Upload-Post`
   - Short description: "Post & schedule to TikTok, Instagram, YouTube, LinkedIn, X and more."
   - Long description: multi-platform publishing, scheduling, analytics, DM funnels.
   - Icon + 3–5 screenshots (use the preview UI).
   - Support email: `info@upload-post.com`, privacy + terms URLs.
6. **Submit** through the dashboard review flow with MCP connectivity details, testing
   guidelines, directory metadata and country availability.
7. After approval, apps roll out to users (rollout began early 2026). Self-serve plugin
   publishing is also coming — keep the Codex plugin (this repo) ready for that channel.

## References
- Apps SDK: https://developers.openai.com/apps-sdk
- Submit apps to the directory: https://help.openai.com/en/articles/20001040-submitting-apps-to-the-chatgpt-app-directory
- Build with the Apps SDK: https://help.openai.com/en/articles/12515353-build-with-the-apps-sdk
