# Upload-Post

This extension connects Gemini CLI to the official Upload-Post MCP server
(`https://mcp.upload-post.com/mcp`). Sign in with your Upload-Post account when
the OAuth prompt opens; you can create a free account at
https://app.upload-post.com.

Use it to publish and schedule videos, photos, carousels, text and documents to
TikTok, Instagram, YouTube, LinkedIn, Facebook, X, Threads, Pinterest, Bluesky,
Reddit, Google Business, Discord and Telegram, and to read comments, DMs and
post analytics.

Working rules:

- Call `list_users` first to see the connected profiles and platforms. Every
  upload needs a profile (`user`) and the platforms to post to.
- Uploads are asynchronous: they return a `request_id` or `job_id`. Poll
  `get_status` until every platform reports success or an error.
- To schedule, pass `scheduled_date` in ISO 8601 with a `timezone`.
- Media can be a public URL or a local file path. For large local files, use
  `create_media_upload` and then `complete_media_upload`.
- Platform-specific options (TikTok privacy, Instagram media type, YouTube
  title and privacy, first comment, …) are documented in each tool's schema and
  at https://docs.upload-post.com.

The bundled skills in `skills/` add ready-made workflows (content funnels,
short-form clipping and viral loops) on top of these tools.
