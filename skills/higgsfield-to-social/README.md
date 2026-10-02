# Higgsfield to Social

Generate an image or video with [Higgsfield](https://higgsfield.ai) and publish it to every
social platform you have connected, in one conversation with your agent.

```
Make a 9:16 Seedance clip of a coffee cup in morning light, score the hook,
and post it to TikTok, Reels and Shorts tomorrow at 9am.
```

The agent generates with the Higgsfield CLI, optionally runs the Virality Predictor, shows you
the result and the caption, and after your OK hands the CDN URL to
[Upload-Post](https://upload-post.com), which posts it (or schedules it) and returns the link
of each post. Nothing is downloaded locally, and every post carries the platform's
AI-generated label where one exists.

## Requirements

- [Higgsfield CLI](https://github.com/higgsfield-ai/cli), logged in (`higgsfield auth login`)
- An [Upload-Post](https://upload-post.com) account with your social accounts connected, used
  through the MCP connector (`https://mcp.upload-post.com/mcp`) or an API key in
  `UPLOAD_POST_API_KEY`

## Platforms

TikTok, Instagram, YouTube, LinkedIn, Facebook, X, Threads, Pinterest, Bluesky, Telegram,
Discord, Mastodon and Google Business Profile.

## Install

```bash
npx skills add Upload-Post/upload-post-skills
```

Or copy `skills/higgsfield-to-social/` into your agent's skills directory.
