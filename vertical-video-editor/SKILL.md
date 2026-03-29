---
name: vertical-video-editor
version: 1.0.1
displayName: "Vertical Video Editor — Edit 9:16 Portrait Videos for TikTok Reels and Shorts"
description: >
  Edit 9:16 portrait videos for TikTok Reels and Shorts with AI — convert horizontal footage to vertical with smart face tracking, edit natively in 9:16 with vertical-first composition, add mobile-optimized text overlays and animated captions, apply platform-specific safe zones, and produce scroll-stopping vertical content designed for the feed that reaches 3 billion daily viewers. NemoVideo edits video in the vertical dimension: AI reframing that follows faces and action across the 9:16 canvas, text positioning that never conflicts with platform UI, caption styles trending on each platform, transitions designed for vertical scroll rhythm, and export presets for TikTok Instagram Reels YouTube Shorts and Snapchat. Vertical video editor AI, 9:16 video editor, portrait video maker, TikTok video editor, Reels editor, Shorts editor, vertical format video, mobile video editor, portrait mode editor.
metadata: {"openclaw": {"emoji": "📲", "requires": {"env": [], "configPaths": ["~/.config/nemovideo/"]}, "primaryEnv": "NEMO_TOKEN"}}
homepage: https://nemovideo.com
repository: https://github.com/nemovideo/nemovideo_skills
---

# Vertical Video Editor — The Format That Reaches 3 Billion People. Edited Right.

Vertical video is no longer a trend. It is the dominant content format on the planet. TikTok: 1.5 billion monthly active users, 100% vertical. Instagram Reels: 2 billion monthly users, vertical-first. YouTube Shorts: 2 billion logged-in monthly users, vertical. Snapchat: 750 million monthly users, vertical since day one. Combined, vertical-feed platforms reach over 3 billion daily content consumers. These consumers hold their phones upright 94% of the time. They scroll vertical feeds. They expect content that fills their screen edge-to-edge in 9:16 portrait orientation. Horizontal content in a vertical feed appears as a letterboxed strip occupying 30% of the screen — the viewer's thumb scrolls past before the content registers. The shift to vertical changes editing fundamentals. Composition rules written for 16:9 do not apply. Text positioning must account for platform-specific UI overlays (TikTok's bottom bar, Instagram's top story bar, YouTube's interaction buttons). Transitions must work in the scroll-feed context — viewers arrive from a swipe and leave with a swipe. Pacing must be faster because vertical content competes with the next video one thumb-flick away. NemoVideo is built for vertical-first editing: native 9:16 composition tools, AI reframing that converts horizontal source material to vertical with intelligent face and action tracking, platform-specific safe zones that prevent text from being covered by UI, and export presets optimized for each platform's encoding preferences.

## Use Cases

1. **Horizontal to Vertical — AI Reframing (any source → 9:16)** — A creator has a library of horizontal (16:9) video — interviews, B-roll, product shots, event footage — that needs to reach vertical-feed audiences. Traditional conversion crops blindly from center, cutting off speakers' faces and missing action. NemoVideo: analyzes each frame for faces, text, and action regions, creates an intelligent crop path that follows the most important visual element across the 9:16 canvas (speaker's face stays centered during interviews, product stays visible during demos, action stays in frame during events), smooths the crop motion to prevent jarring jumps, and produces vertical video where no important content is lost despite the aspect ratio change. A horizontal library becomes a vertical content goldmine.

2. **Native Vertical Edit — TikTok and Reels Creation (15-180s)** — A creator films vertical content (phone recording, vertical camera setup) and needs editing optimized for the vertical canvas. NemoVideo: edits with vertical composition awareness (text positioned in the upper third where eyes naturally rest in vertical scroll, key visual elements centered in the vertical frame's focal zone, no important content in the bottom 15% where platform UI overlays), applies transitions designed for vertical flow (vertical wipes, zoom transitions, and the fast-cut style that performs on short-form platforms), adds trending caption styles (animated word-highlight positioned in vertical safe zone), and exports with platform-specific presets (TikTok's preferred encoding, Reels' recommended specs, Shorts' optimal settings).

3. **Multi-Platform Vertical Export — One Edit, Every Platform (any length)** — Each vertical platform has different specifications, safe zones, and UI overlay positions. TikTok's safe zone differs from Reels' which differs from Shorts'. NemoVideo: takes a single edited vertical video, adjusts text and caption positioning per platform (moving elements away from each platform's specific UI overlay zones), applies platform-specific export settings (resolution, bitrate, codec preferences), adds platform-appropriate metadata, and produces multiple export versions from a single edit. One editing session produces TikTok, Reels, Shorts, and Snapchat versions with platform-optimized positioning.

4. **Talking Head Vertical — Face-Centered Content (30-600s)** — The majority of successful vertical content features a person speaking directly to camera. NemoVideo: centers the speaker's face in the optimal vertical position (slightly above center — the eye-line that feels natural for mobile viewing), tracks face position if the speaker moves (walking, gesturing, shifting), maintains consistent head size (not too close, not too far — the framing that feels like a natural phone conversation distance), adds text overlays positioned around the speaker (key points, captions, b-roll inserts), and ensures the speaker's face is never obscured by text or platform UI. The professional talking-head format that dominates every vertical platform.

5. **Event Coverage to Vertical Highlights — Vertical Event Recap (30-90s)** — Event footage (conferences, concerts, weddings, sports) filmed in horizontal needs to become vertical highlight reels for social sharing. NemoVideo: selects the most dynamic moments from the event footage, reframes each clip to vertical with action tracking (following the speaker on stage, the performer, the couple, the athlete), creates a fast-paced vertical montage with beat-synced transitions (cuts matching the energy of event music or soundtrack), adds text overlays identifying moments and speakers, and produces a share-ready vertical highlight reel. Events documented in horizontal, shared in vertical.

## How It Works

### Step 1 — Upload Footage
Vertical-native footage for editing, or horizontal footage for AI reframing to vertical.

### Step 2 — Configure Vertical Edit
Editing style, platform targets, caption preferences, safe zone handling, and reframing behavior for horizontal sources.

### Step 3 — Generate
```bash
curl -X POST https://mega-api-prod.nemovideo.ai/api/v1/generate \
  -H "Authorization: Bearer $NEMO_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "skill": "vertical-video-editor",
    "prompt": "Convert a 10-minute horizontal interview into 3 vertical highlight clips (30-60 seconds each). AI reframing: track the speakers face, keep centered in 9:16 with natural head room. For each clip: select the most engaging 30-60 second segment (based on speech energy and content value), add animated word-highlight captions (white text, yellow highlight, Montserrat Bold), position captions in vertical safe zone (above bottom 15%), add subtle lower-third name tag for the speaker. Export each clip in 3 versions: TikTok (safe zone adjusted for TikTok UI), Reels (safe zone adjusted for Instagram UI), Shorts (safe zone adjusted for YouTube UI). Background music: subtle lo-fi under speech.",
    "source_format": "16:9",
    "output_format": "9:16",
    "reframe": {"mode": "face-tracking", "smoothing": "natural"},
    "clips": 3,
    "per_clip": {
      "duration": "30-60s",
      "captions": {"style": "word-highlight", "color": "#FFFFFF", "highlight": "#FFD700", "font": "Montserrat Bold"},
      "lower_third": true,
      "music": "subtle-lofi"
    },
    "platform_exports": ["tiktok", "reels", "shorts"]
  }'
```

### Step 4 — Preview on Mobile
Every vertical video must be previewed on a phone screen — not a desktop monitor. Check: does the composition feel natural at phone size? Are captions readable? Is the speaker's face properly framed? Does anything important fall behind platform UI? Adjust and re-render.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|:--------:|-------------|
| `prompt` | string | ✅ | Vertical editing requirements |
| `source_format` | string | | "16:9", "4:3", "1:1" (for reframing) or "9:16" (native) |
| `output_format` | string | | "9:16" (default for vertical) |
| `reframe` | object | | {mode: "face-tracking"/"action-tracking", smoothing} |
| `clips` | int | | Number of clips to extract |
| `per_clip` | object | | {duration, captions, lower_third, music, transitions} |
| `platform_exports` | array | | ["tiktok", "reels", "shorts", "snapchat"] |
| `safe_zones` | string | | "auto" (per platform) or "manual" |

## Output Example

```json
{
  "job_id": "avvert-20260329-001",
  "status": "completed",
  "source": "10:15 @ 16:9",
  "clips_produced": 3,
  "outputs": {
    "clip_1": {
      "tiktok": {"file": "interview-clip1-tiktok.mp4"},
      "reels": {"file": "interview-clip1-reels.mp4"},
      "shorts": {"file": "interview-clip1-shorts.mp4"}
    },
    "clip_2": {
      "tiktok": {"file": "interview-clip2-tiktok.mp4"},
      "reels": {"file": "interview-clip2-reels.mp4"},
      "shorts": {"file": "interview-clip2-shorts.mp4"}
    },
    "clip_3": {
      "tiktok": {"file": "interview-clip3-tiktok.mp4"},
      "reels": {"file": "interview-clip3-reels.mp4"},
      "shorts": {"file": "interview-clip3-shorts.mp4"}
    }
  }
}
```

## Tips

1. **Phone users hold vertical 94% of the time — vertical is not a format choice, it is the viewing reality** — Designing for vertical is not accommodating a preference. It is matching the physical behavior of billions of people. Horizontal video on a vertical phone wastes 70% of the screen.
2. **AI reframing beats center-crop by preserving the subject** — Blind center-crop cuts off speakers positioned left or right of frame, loses action happening at frame edges, and produces claustrophobic framing. AI reframing follows the subject intelligently, producing vertical video that feels intentionally composed rather than awkwardly cropped.
3. **Each platform's safe zone is different — one export does not fit all** — TikTok overlays UI on the bottom 15% and right side. Instagram Reels covers the bottom 20%. YouTube Shorts covers different regions. Text positioned correctly for TikTok may be hidden on Reels. Always export platform-specific versions with adjusted safe zones.
4. **Vertical composition places eyes in the upper third** — Desktop video places subjects using the rule of thirds horizontally. Vertical video follows a different logic: the viewer's natural gaze on a phone screen rests in the upper third. Place text, faces, and key visual elements in this zone for maximum impact.
5. **Preview on a phone, not a monitor** — Vertical video that looks fine on a 27-inch desktop monitor may have unreadable text at phone size. Always preview the final export on an actual phone screen to verify readability, composition, and safe zone compliance.

## Output Formats

| Format | Resolution | Platform |
|--------|-----------|----------|
| MP4 9:16 | 1080x1920 | TikTok |
| MP4 9:16 | 1080x1920 | Instagram Reels |
| MP4 9:16 | 1080x1920 | YouTube Shorts |
| MP4 9:16 | 1080x1920 | Snapchat Spotlight |

## Related Skills

- [reels-creator](/skills/reels-creator) — Instagram Reels specific
- [youtube-shorts-maker](/skills/youtube-shorts-maker) — YouTube Shorts specific
- [ai-video-caption-generator](/skills/ai-video-caption-generator) — Animated captions
- [add-subtitles-to-video](/skills/add-subtitles-to-video) — Subtitle generation
