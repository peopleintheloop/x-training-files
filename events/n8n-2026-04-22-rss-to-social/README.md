# n8n Atlanta Community Workshop · April 22, 2026

**Event:** n8n Atlanta Community Workshop
**Hosts:** Alicia Graham & Nina Thomas
**Date:** April 22, 2026
**Location:** ATDC · 75 5th St NW 2nd Floor · Atlanta, GA
**Time:** 5:30 PM – 8:30 PM

---

## What This Folder Contains

These workflow files were built live at this event. Everything here is ready to import into your n8n account and use immediately.

| File | What It Does |
|------|-------------|
| `level1-rss-to-email-template.json` | Watches an RSS feed, writes 3 platform-specific social posts via Claude, and sends them to your email automatically |
| `level2-brand-voice-rss-to-email-template.json` | Extends Level 1 with two upgrades: Claude writes posts in your brand's defined voice using a custom system prompt, then generates an image prompt that gets sent to Cloudflare Workers AI (Flux model) to create a matching visual. The email delivers the AI-generated image embedded inline alongside all three social posts, ready to use |
| `claude-brand-voice-prompt.md` | The brand voice system prompt template — fill it out once and paste into the Claude Model node system message |
| `claude-skill.md` | A Claude Project system prompt that turns Claude into your personal n8n assistant (bonus take-home) |
| `html-email-reference.md` | How to use HTML in the Gmail node — formatting, templates, and n8n expression syntax (bonus reference) |

---

## How to Import a Workflow

1. Log into your n8n account at [n8n.io](https://n8n.io) — free account works
2. Go to **Workflows** in the left sidebar
3. Click the **+** button and select **Import from file**
4. Upload the `.json` file
5. The workflow opens with all nodes and documentation already placed
6. Connect your credentials and update the email address in the Gmail node
7. Run a test before activating

---

## What You Need

**For both workflows:**
- n8n account (free tier works)
- Anthropic API key — get yours free at [console.anthropic.com](https://console.anthropic.com)
- Google account connected via OAuth2 in n8n

**For Level 2 only:**
- A completed `claude-brand-voice-prompt.md` — fill in every field in brackets with your own information
- Cloudflare Workers AI account (free tier) — get yours at [dash.cloudflare.com](https://dash.cloudflare.com). Go to My Profile → API Tokens → Create Token. Use the "Workers AI" template. Copy the Bearer token and add it to n8n Credentials as an HTTP Bearer Auth credential.

---

## The Concepts Covered at This Event

**Why n8n instead of just Claude**
Claude is a thinking tool. n8n is a plumbing tool. When you need something to run automatically on a schedule, respond to a trigger, or connect multiple services without you being present — that is n8n's job. Claude handles the intelligence inside the workflow.

**Claude Projects vs the Claude node in n8n**
A Claude Project lives in Claude.ai and holds your brand voice, your instructions, and your context permanently. The Claude node in n8n calls the Anthropic API directly and runs Claude as one step inside a larger automated process. They serve different purposes and work well together.

**Tokens and APIs — the short version**
An API is how two software tools talk to each other. When n8n calls Claude, it sends a request through the Anthropic API. Tokens are how AI models measure text — inputs and outputs both cost tokens, which is why API usage has a cost. The free Claude.ai interface gives you a set number of messages. The API gives you more control and works inside automations, but charges per token used.

**Plan before you automate**
Map the workflow on paper or in Miro before you touch n8n. Know what triggers it, what data moves through it, and what the output looks like. Building before planning is the most common reason workflows break.

---

## Get All Files From This Event

All files, import-ready workflows, and setup instructions are at:

**[peopleintheloop.app/n8n_0422](https://peopleintheloop.app/n8n_0422)**

Join People in the Loop at [peopleintheloop.app](https://peopleintheloop.app) to get new workflows from every event delivered to your inbox.

---

## About the Creators

**Nina Thomas**
AI Strategist & Educator | n8n Community Ambassador | Miro Hero Ambassador
Founder, People in the Loop
[ninathomas.ai](https://ninathomas.ai) · [linkedin.com/in/ninathomas](https://linkedin.com/in/ninathomas)

**Alicia Graham**
AI Economist | n8n Ambassador
[linkedin.com/in/aliciagraham](https://linkedin.com/in/aliciagraham)

---

## License

See `LICENSE.md` in this folder for full terms.
Personal and educational use is free. Commercial use requires attribution.
