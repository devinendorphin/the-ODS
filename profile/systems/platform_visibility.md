# Platform Visibility Monitoring

*[PRIVATE data fields marked; schema is public]*

The term "shadow ban" covers a spectrum of platform suppressions — most of which platforms deny exist while implementing constantly. This document maps the known suppression types, detection methods, and the monitoring system to catch them early.

---

## The Problem

A reach drop from 60–100 live viewers to near-zero is not random noise. It is either:

1. **Algorithmic suppression** — your content has been flagged or deprioritized by the recommendation system
2. **Shadow restriction** — a soft penalty applied to your account that limits distribution without notifying you
3. **Content-specific throttling** — a specific video/stream was flagged, which then affected account-wide reach
4. **Platform algorithm change** — the rules changed; your content no longer fits the pattern being promoted
5. **Engagement signal collapse** — early engagement dropped (for whatever reason), and the algorithm stopped promoting because the early signals were weak

The problem is that platforms deliberately obscure which of these is happening. The monitoring system's job is to make the invisible visible.

---

## Suppression Types by Platform

### YouTube (Live Streams specifically)
| Type | What happens | How to detect |
|---|---|---|
| Live stream recommendation suppression | Stream doesn't appear in "Live Now" or subscriber feeds | Check logged-out / incognito — does stream appear in search? |
| Age restriction | Stream restricted to verified 18+ viewers | Check your Video Manager for age gate labels |
| Limited state | Flagged content, limited in recommendations | YouTube Studio → Content → check for "Limited" label |
| Community Guidelines strike | Removes monetization, can affect all content | Studio → Dashboard → policy section |
| Shadowban | Subscribers not notified of live streams | Ask a subscribed friend if they saw the notification |

**Key insight on the viewer drop:** YouTube's live recommendation is heavily dependent on the first 5–10 minutes of a stream. If early concurrent viewers are low (or if notifications don't fire), the algorithm doesn't promote it further. The notification system itself is unreliable — YouTube has acknowledged that not all subscribers receive notifications.

### Twitter/X
| Type | What happens | How to detect |
|---|---|---|
| Search shadow ban | Tweets don't appear in search results | Search your username from a logged-out browser |
| Ghost ban | Tweets hidden from everyone but you | Ask someone who doesn't follow you to view your profile |
| Reply deboosting | Replies buried under "Show more replies" | Check reply visibility from an account that doesn't follow you |
| Sensitive content flag | Tweets only shown to users who've opted into sensitive content | Check account settings for sensitive content labels |

### Instagram
| Type | What happens | How to detect |
|---|---|---|
| Hashtag ban | Posts using flagged hashtags don't appear in hashtag feeds | Search your hashtag from a non-following account |
| Explore suppression | Posts stop appearing in Explore | Check post reach in insights — "From explore" goes to zero |
| "Account suggested to fewer people" | Instagram tells you directly (rare but happens) | Check Professional Dashboard |
| Cascade effect | Instagram suppression propagates to Threads and Facebook | Check reach on all three simultaneously |

---

## Detection Protocols

### Protocol 1: The Logged-Out Test
*Run this immediately after any suspected suppression event.*

1. Open a private/incognito browser window (not logged into any account)
2. Search for your handle on each platform
3. Search for your most recent content by title or keyword
4. Note: does it appear? At what position? Are there content warnings?
5. Log results in the Incident Log below

### Protocol 2: The Friend Test
*For detecting account-level suppression that logged-out tests miss.*

Ask someone who follows you on each platform to:
- Confirm they received the most recent notification
- Search your name from their account
- Confirm they can see your most recent posts without filtering

Ask someone who does NOT follow you to:
- Search your name
- Tell you what they see on your profile page

### Protocol 3: The Reach Comparison Log
*The most important long-term tool — making anomalies visible over time.*

Track these metrics after every significant post or live stream:

```
Date:
Platform:
Content type: [live stream / video / post / reel]
Content topic/keywords:
Views at 1 hour:
Views at 24 hours:
Views at 7 days:
Live peak viewers (if applicable):
Notification fired: [yes / no / unknown]
Reach sources (from analytics): [followers / non-followers / hashtags / explore / search / recommended]
Notes:
```

A sudden drop in the "non-followers" reach percentage is the clearest signal of recommendation suppression. If your content reaches followers but not new people, the algorithm has stopped promoting you without telling you.

### Protocol 4: The Content Correlation Test
*To identify whether suppression is content-specific or account-wide.*

When you notice a drop:
1. What was the last piece of content posted before the drop?
2. What keywords, hashtags, or topics did it use?
3. Post something deliberately benign (unrelated to any potentially flagged topics) and measure its reach
4. If benign content performs normally, the suppression is content-specific
5. If benign content is also suppressed, the suppression is account-level

---

## Incident Log

| Date | Platform | Type of drop | Suspected cause | Detected how | Resolved |
|---|---|---|---|---|---|
| [unknown date] | YouTube | Live viewers: 60–100 → ~0 | Unknown — algorithmic or shadow restriction | Direct observation | Unknown |

*(Continue logging all incidents)*

---

## Monitoring Automation (To Build)

The manual protocols above are necessary now. The goal is to automate them:

### Phase 1: Reach Tracking Dashboard
- Script that pulls analytics from YouTube Studio API, Instagram Graph API, and Twitter API
- Logs metrics to a local database after each post/stream
- Flags anomalies (>50% drop from rolling average) with an alert
- Produces a weekly reach report

### Phase 2: Visibility Checker
- Script that checks account/content visibility from "outside" (using a secondary test account or unauthenticated requests where permitted)
- Runs on a schedule, alerts on changes
- Cross-references against known shadow ban detection endpoints

### Phase 3: Content Correlation Analysis
- Analyzes which content topics correlate with reach drops
- Identifies patterns: specific hashtags, keywords, or posting times that precede suppression events
- Produces a "content risk profile" that helps predict suppression before it happens

### Phase 4: Appeal and Escalation Workflows
- When suppression is detected, the agent drafts the appropriate appeal
- Platform-specific: YouTube's content appeal, Instagram's "Request Review," Twitter's appeal process
- Escalation path: if appeals fail, agent helps document for external reporting (journalist contacts, digital rights organizations)

---

## Resources

- **YouTube Studio analytics**: youtube.com/analytics
- **Instagram Professional Dashboard**: instagram.com/professional_dashboard
- **Twitter Analytics**: analytics.twitter.com
- **Electronic Frontier Foundation (EFF)**: Platform accountability and appeals guidance
- **Fight for the Future**: Digital rights advocacy
- **ACLU Digital Rights Project**: For cases with civil liberties implications
