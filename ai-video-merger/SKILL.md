---
name: ai-video-merger
version: "1.0.0"
displayName: "AI Video Merger — Combine Multiple Clips Into One Seamless Video"
description: >
  Tired of juggling separate video files and struggling to stitch them together without losing quality? The ai-video-merger skill takes the frustration out of combining clips by intelligently joining multiple videos into a single, cohesive output. Whether you're assembling event footage, compiling social media content, or building a highlight reel, this skill handles mp4, mov, avi, webm, and mkv formats with ease. Features include sequential merging, custom ordering, and quality-preserving output — built for content creators, educators, and marketers who need results fast.
metadata: {"openclaw": {"emoji": "🎬", "requires": {"env": ["NEMO_TOKEN"], "configPaths": ["~/.config/nemovideo/"]}, "primaryEnv": "NEMO_TOKEN"}}
apiDomain: https://mega-api-prod.nemovideo.ai
homepage: https://nemovideo.com
repository: https://github.com/nemovideo/nemovideo_skills
---

## Getting Started

> Welcome! I'm your AI Video Merger — ready to combine your video clips into one seamless, polished file. Drop your videos and tell me how you'd like them ordered, and let's get merging!

**Try saying:**
- "Merge these three mp4 clips in this order: intro.mp4, main_talk.mp4, outro.mp4 into a single video"
- "Combine my wedding ceremony and reception footage into one continuous video file"
- "Join all five tutorial segments into one complete course video, keeping them in sequence"

On first use, the skill connects to NemoVideo automatically:
1. Check for `NEMO_TOKEN` env var, or acquire one via `https://mega-api-prod.nemovideo.ai/api/auth/anonymous-token` (100 free credits)
2. Persist a Client-ID to `~/.config/nemovideo/client_id` for rate-limit tracking (UUID only, no secrets)
3. Create a session and start working immediately

# Merge Any Videos Into One Polished Final Cut

Creating a single, flowing video from multiple separate clips used to mean wrestling with complex editing software, dealing with format incompatibilities, and spending hours on a task that should take minutes. The AI Video Merger skill changes that entirely by giving you a straightforward, intelligent way to combine your footage without the usual headaches.

Whether you have two clips or twenty, this skill sequences them in your chosen order and outputs a clean, unified video file. It respects the original resolution and audio of your source material, so you're not sacrificing quality just to get things joined together. You can mix clips shot on different devices or exported from different platforms — the skill handles the format differences behind the scenes.

This is especially useful for content creators building episode compilations, trainers assembling multi-part tutorial videos, or event videographers combining ceremony and reception footage into one shareable file. The goal is simple: you bring the clips, the skill brings them together.

### Environment

| Variable | Default | Purpose |
|----------|---------|---------|
| `NEMO_TOKEN` | Auto-acquired on first use (100 free credits, 7-day expiry) | API authentication |
| `NEMO_API_URL` | `https://mega-api-prod.nemovideo.ai` | API base URL |

## Routing Your Merge Requests

When you describe a merge task — whether it's trimming, sequencing, or blending multiple clips — the skill interprets your intent and routes the request to the appropriate NemoVideo merge pipeline automatically.

| User says... | Action | Skip SSE? |
|-------------|--------|----------|
| "export" / "导出" / "download" / "send me the video" | → §3.5 Export | ✅ |
| "credits" / "积分" / "balance" / "余额" | → §3.3 Credits | ✅ |
| "status" / "状态" / "show tracks" | → §3.4 State | ✅ |
| "upload" / "上传" / user sends file | → §3.2 Upload | ✅ |
| Everything else (generate, edit, add BGM…) | → §3.1 SSE | ❌ |

## NemoVideo API Reference

The NemoVideo backend processes each merge job by ingesting your source clips, applying the requested transitions and sequencing logic, then rendering a single unified output file. All clip handling, frame alignment, and codec normalization happen server-side, so no local processing is required.

**Required headers** on all requests: `X-Skill-Source: $SKILL_NAME`, `X-Skill-Version: $SKILL_VERSION`, `X-Skill-Platform: $SKILL_SOURCE`

**Create session**: `POST $API/api/tasks/me/with-session/nemo_agent` — returns `task_id` and `session_id`

**Send message (SSE)**: `POST $API/run_sse` with `session_id` and user message. Stream responses; ~30% of edits return no text (query state to confirm changes).

**Upload**: `POST $API/api/upload-video/nemo_agent/me/<sid>` — file or URL upload. Supports: mp4, mov, avi, webm, mkv, jpg, png, gif, webp, mp3, wav, m4a, aac.

**Check credits**: `GET $API/api/credits/balance/simple`

**Query state**: `GET $API/api/state/nemo_agent/me/<sid>/latest` — check draft, tracks, generated media

**Export**: `POST $API/api/render/proxy/lambda` — export does NOT cost credits. Poll `GET $API/api/render/proxy/lambda/<id>` until `status: completed`.

**Task link**: `$WEB/workspace/claim?token=$TOKEN&task={task_id}&session={session_id}&skill_name=$SKILL_NAME&skill_version=$SKILL_VERSION&skill_source=$SKILL_SOURCE`

### Common Errors

If your token has expired, simply re-authenticate through the ClawHub connection settings to restore access. A 'session not found' error means your previous merge session timed out — start a fresh session and re-upload your clips. If you're out of credits, visit nemovideo.ai to register or top up your account before submitting another merge job.

## Common Workflows

The most frequent use case for the AI Video Merger is assembling multi-part recordings into a single deliverable. Podcasters who record intro segments separately from main content, for example, can merge all parts into one upload-ready file in seconds.

Another popular workflow involves social media repurposing — combining several short clips from the same event into one longer recap video suitable for YouTube or a website. This saves time compared to re-editing everything from scratch in a timeline editor.

Educators and course creators also rely on this skill heavily. Recording lectures in segments is common, and merging them into a single cohesive lesson video makes distribution and student viewing far more straightforward. The skill preserves chapter-like pacing naturally, since each original clip retains its own rhythm.

## Performance Notes

Merge processing time scales with the total duration and file size of your input clips. A set of short clips under five minutes total will process quickly, while longer source files — such as full-length event recordings — may take more time to join and finalize.

For best results, try to use clips with matching frame rates when possible. While the AI Video Merger can handle mixed-rate inputs, consistent frame rates across clips produce the smoothest playback in the final output.

Audio tracks are preserved and merged continuously alongside video, so voiceovers, background music, and ambient sound carry through naturally from clip to clip. If you notice any audio sync concerns in the output, re-submitting with clips exported at a consistent bitrate typically resolves the issue.

## Quick Start Guide

Getting started with the AI Video Merger is straightforward. Begin by gathering all the video clips you want to combine — supported formats include mp4, mov, avi, webm, and mkv, so there's no need to pre-convert your files.

Next, tell the skill the order you want the clips merged. You can specify this by listing filenames in sequence, describing the desired order, or simply uploading them in the correct arrangement. Being explicit about order avoids any guesswork.

Once the merge is complete, you'll receive a single output video file. If the result isn't quite right — say you want to reorder two segments or drop one clip entirely — just describe the change and the skill will re-process accordingly. Think of it as an iterative conversation rather than a one-shot command.
