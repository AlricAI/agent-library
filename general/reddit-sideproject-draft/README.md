# Reddit Sideproject Draft

> **STATUS: DRAFT — DO NOT POST UNTIL JOSHUA APPROVES**

---

## Target

- **Subreddit:** r/SideProject
- **Flair:** Show Off
- **Tone:** Humble, authen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Show & Tell: Built a dating app with bank-level identity verification (electrician turned dev, 100% self-taught)

**STATUS: DRAFT — DO NOT POST UNTIL JOSHUA APPROVES**

---

## Target

- **Subreddit:** r/SideProject
- **Flair:** Show Off
- **Tone:** Humble, authentic, educational — NOT promotional

---

## Title

> Show & Tell: Built a dating app with bank-level identity verification (electrician turned dev, 100% self-taught)

## Body

Hey r/SideProject,

I'm a licensed electrician from Kentucky who taught himself to code over the past year and a half. Wanted to share what I've been building and get some honest feedback.

**The problem that annoyed me into learning to code:**

I kept running into fake profiles and bots on dating apps. After one too many conversations that turned out to be automated, I started looking into _why_ dating apps don't verify identity. The answer was pretty simple — it's expensive, and inflated user counts help their metrics.

**What I built:**

YouAndINotAI — a dating platform where every user goes through identity verification before they can create a profile. Not just email/phone verification (bots bypass that trivially). Actual identity verification using Plaid's Identity API — the same infrastructure that Venmo, Cash App, and major banks use to confirm who someone is.

The verification system (I call it V8 Cloud) runs multiple checks:

- Government ID verification
- Liveness detection
- Bank identity cross-reference via Plaid
- Device fingerprinting
- Continuous monitoring

If any check fails, you don't get a profile. Period.

**The technical journey (for the devs here):**

Starting from zero was humbling. I went from not knowing what a variable was to building a full-stack app with payment processing and third-party API integrations. The learning curve was steep, but honestly — trade work teaches you how to troubleshoot and read documentation, which turns out to be 80% of programming.

Tools that saved me: AI assistants for debuggi

*[truncated — see source for full prompt]*