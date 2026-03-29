---
name: youtube-monetization-video
version: "1.0.0"
displayName: "YouTube Monetization Video Creator — Build Ad-Ready Videos That Earn"
description: >
  Turn raw footage into polished, monetization-ready YouTube videos that meet platform standards and attract advertiser spend. This youtube-monetization-video skill analyzes your uploads, optimizes pacing, flags demonetization risks, and structures content for maximum CPM potential. Built for creators serious about revenue — whether you're a solo vlogger or a growing channel. Supports mp4, mov, avi, webm, and mkv formats.
metadata: {"openclaw": {"emoji": "💰", "requires": {"env": ["NEMO_TOKEN"], "configPaths": ["~/.config/nemovideo/"]}, "primaryEnv": "NEMO_TOKEN"}}
apiDomain: https://mega-api-prod.nemovideo.ai
homepage: https://nemovideo.com
repository: https://github.com/nemovideo/nemovideo_skills
---

## Getting Started

> Welcome! Ready to turn your video into a monetization-optimized YouTube upload that earns more per view? Drop your footage here and let's build something ad-ready together.

**Try saying:**
- "Analyze my vlog footage and flag any sections that could get demonetized before I upload"
- "Restructure my 18-minute video to maximize mid-roll ad placement and viewer retention"
- "Review my YouTube video and suggest edits to make it more advertiser-friendly for a higher CPM"

On first use, the skill connects to NemoVideo automatically:
1. Check for `NEMO_TOKEN` env var, or acquire one via `https://mega-api-prod.nemovideo.ai/api/auth/anonymous-token` (100 free credits)
2. Persist a Client-ID to `~/.config/nemovideo/client_id` for rate-limit tracking (UUID only, no secrets)
3. Create a session and start working immediately

# Make Every Upload Work Harder for Your Revenue

Most creators upload videos and hope the algorithm rewards them. This skill takes a smarter approach — it looks at your footage through the lens of YouTube's monetization policies and advertiser preferences, helping you understand exactly what's working and what might be quietly costing you revenue.

Whether you're trying to hit the 4,000 watch-hour threshold, avoid the dreaded yellow dollar icon, or simply structure your video in a way that keeps viewers watching long enough to trigger mid-roll ads, this tool gives you actionable guidance at every step. It evaluates your content for ad-friendliness, suggests edits that improve retention, and highlights sections that could trigger content flags before you ever hit publish.

This isn't just about avoiding violations — it's about building videos that advertisers actively want to appear on. Creators who consistently produce clean, structured, high-retention content earn significantly more per thousand views. This skill helps you become that kind of creator, systematically and without guesswork.

### Environment

| Variable | Default | Purpose |
|----------|---------|---------|
| `NEMO_TOKEN` | Auto-acquired on first use (100 free credits, 7-day expiry) | API authentication |
| `NEMO_API_URL` | `https://mega-api-prod.nemovideo.ai` | API base URL |

## Routing Your Monetization Requests

Every prompt you send — whether you're scripting an ad-friendly intro, structuring mid-roll placement hooks, or building watch-time retention segments — gets routed directly to the NemoVideo generation engine based on detected monetization intent.

| User says... | Action | Skip SSE? |
|-------------|--------|----------|
| "export" / "导出" / "download" / "send me the video" | → §3.5 Export | ✅ |
| "credits" / "积分" / "balance" / "余额" | → §3.3 Credits | ✅ |
| "status" / "状态" / "show tracks" | → §3.4 State | ✅ |
| "upload" / "上传" / user sends file | → §3.2 Upload | ✅ |
| Everything else (generate, edit, add BGM…) | → §3.1 SSE | ❌ |

## NemoVideo API Under The Hood

The NemoVideo backend parses your YouTube monetization parameters — CPM targets, ad break positioning, audience retention curves — and assembles video assets optimized for AdSense compliance and algorithmic ranking. It handles everything from skippable ad pacing to end-screen CTA timing without requiring manual encoding.

**Required headers** on all requests: `X-Skill-Source: $SKILL_NAME`, `X-Skill-Version: $SKILL_VERSION`, `X-Skill-Platform: $SKILL_SOURCE`

**Create session**: `POST $API/api/tasks/me/with-session/nemo_agent` — returns `task_id` and `session_id`

**Send message (SSE)**: `POST $API/run_sse` with `session_id` and user message. Stream responses; ~30% of edits return no text (query state to confirm changes).

**Upload**: `POST $API/api/upload-video/nemo_agent/me/<sid>` — file or URL upload. Supports: mp4, mov, avi, webm, mkv, jpg, png, gif, webp, mp3, wav, m4a, aac.

**Check credits**: `GET $API/api/credits/balance/simple`

**Query state**: `GET $API/api/state/nemo_agent/me/<sid>/latest` — check draft, tracks, generated media

**Export**: `POST $API/api/render/proxy/lambda` — export does NOT cost credits. Poll `GET $API/api/render/proxy/lambda/<id>` until `status: completed`.

**Task link**: `$WEB/workspace/claim?token=$TOKEN&task={task_id}&session={session_id}&skill_name=$SKILL_NAME&skill_version=$SKILL_VERSION&skill_source=$SKILL_SOURCE`

### Common Errors

If your token expires mid-session, simply re-authenticate through the ClawHub connector to restore full access to the monetization pipeline. A 'session not found' response means your context window reset — start a fresh session and restate your video monetization goals. Out of credits? Head to nemovideo.ai to register or top up so your ad-ready video builds keep rolling.

## Troubleshooting

If the skill flags a section of your video as a monetization risk but you believe it complies with YouTube's policies, check the specific reason provided. Some flags are precautionary — particularly around background music, news clips, or strong language — and you may be able to resolve them by trimming a few seconds or adjusting audio levels before re-uploading.

For videos that are longer than 30 minutes, processing may take slightly more time. If your file appears stuck, try splitting it into two segments and running each separately — this also gives you more granular feedback per section.

If you're seeing unexpected results on videos that have previously monetized fine on your channel, check whether your footage includes any newly licensed music or third-party clips. Copyright conditions change, and what was clear six months ago may now be flagged. The skill detects these based on content patterns, so use the output as a pre-publish checklist, not a guarantee. When in doubt, cross-reference with YouTube Studio's own checks after uploading as unlisted.

## Tips and Tricks

To get the most out of the youtube-monetization-video skill, upload your footage as early in the editing process as possible — even rough cuts work. The earlier you catch demonetization risks, the less rework you'll need later.

Pay close attention to the ad placement recommendations. YouTube's mid-roll ads only trigger on videos over 8 minutes, but placement matters just as much as length. The skill will identify natural pause points in your content where mid-rolls are least likely to cause viewers to drop off — use those suggestions, they're based on pacing analysis, not guesswork.

If you're uploading content in sensitive categories like finance, health, or news commentary, run it through this skill before finalizing your title and thumbnail too. Sometimes a small wording change in your script — flagged here — is the difference between full green monetization and limited ads. Consistency across uploads also builds your channel's advertiser trust score over time, so treat every video as part of a longer strategy.
