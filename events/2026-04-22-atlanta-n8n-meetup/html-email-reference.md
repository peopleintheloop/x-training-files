# HTML Email Reference
**For: n8n Meetup Atlanta — April 22, 2026**
Prepared by People in the Loop

---

## Why HTML in Your Email Node?

When n8n sends an email via the Gmail node, it can send plain text or HTML. HTML lets you add formatting, bold text, headings, and links so your emails look polished instead of like a raw AI output.

The Gmail node has a toggle: **Email Type → HTML**. Once you flip it, everything you send is rendered by the recipient's email client just like a webpage.

---

## Starter Template

Copy this into the Gmail node's **Message** field. Replace anything in `[brackets]` with real content or n8n expressions.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 0 auto;
      color: #222222;
      line-height: 1.6;
    }
    h2 {
      color: #EA4B25;
      margin-top: 0;
    }
    .section {
      margin-bottom: 24px;
    }
    .platform {
      font-weight: bold;
      color: #EA4B25;
    }
    .post-content {
      background-color: #f5f5f5;
      border-left: 4px solid #EA4B25;
      padding: 12px 16px;
      margin: 8px 0;
      border-radius: 4px;
    }
    .footer {
      margin-top: 32px;
      padding-top: 16px;
      border-top: 1px solid #E0DBD4;
      font-size: 12px;
      color: #888888;
    }
  </style>
</head>
<body>

  <h2>New Content Alert: {{ $json.title }}</h2>

  <div class="section">
    <p><strong>Article:</strong> <a href="{{ $json.link }}">{{ $json.title }}</a></p>
    <p><strong>Published:</strong> {{ $json.pubDate }}</p>
  </div>

  <div class="section">
    <p class="platform">Instagram</p>
    <div class="post-content">{{ $json.instagram }}</div>
  </div>

  <div class="section">
    <p class="platform">LinkedIn</p>
    <div class="post-content">{{ $json.linkedin }}</div>
  </div>

  <div class="section">
    <p class="platform">X (Twitter)</p>
    <div class="post-content">{{ $json.twitter }}</div>
  </div>

  <div class="footer">
    Generated automatically by your n8n workflow.<br>
    Powered by People in the Loop.
  </div>

</body>
</html>
```

---

## Key HTML Tags to Know

These are the tags you'll actually use in emails. You don't need to know all of HTML — just these.

**Text formatting**

```html
<strong>bold text</strong>
<em>italic text</em>
<br>           <!-- line break (no closing tag needed) -->
<p>paragraph</p>
```

**Links**

```html
<a href="https://example.com">click here</a>
```

**Headings** (h1 is biggest, h6 is smallest)

```html
<h1>Big heading</h1>
<h2>Medium heading</h2>
<h3>Small heading</h3>
```

**Containers** (use these to group and style sections)

```html
<div style="background-color: #f5f5f5; padding: 12px;">
  Content goes here
</div>
```

**Lists**

```html
<ul>
  <li>Unordered item</li>
  <li>Another item</li>
</ul>

<ol>
  <li>First item</li>
  <li>Second item</li>
</ol>
```

---

## Inline Styles vs. the Style Block

There are two ways to style HTML in emails.

**Option 1 — Style block** (what the template uses): you write styles once at the top and reference them by class name. Cleaner. Works great for most email clients.

```html
<style>
  .highlight { color: red; font-weight: bold; }
</style>
...
<p class="highlight">This text is red and bold.</p>
```

**Option 2 — Inline styles**: you write styles directly on each element. More verbose but guaranteed to work in every email client, including older Outlook versions.

```html
<p style="color: red; font-weight: bold;">This text is red and bold.</p>
```

**Tip:** Gmail renders both fine. If you're sending to corporate addresses (Outlook), use inline styles to be safe.

---

## Connecting n8n Expressions

Inside your HTML, you can use any n8n expression the same way you would in plain text. Just drop them in like variables.

```html
<!-- Article title as a link -->
<a href="{{ $json.link }}">{{ $json.title }}</a>

<!-- Show a field from Claude's output -->
<div class="post-content">{{ $json.instagram }}</div>

<!-- Date formatting -->
<p>Published: {{ $json.pubDate }}</p>
```

The key thing: n8n processes the expressions first, then sends the completed HTML to Gmail. Your recipient never sees the `{{ }}` syntax.

---

## Quick Customization Tips

**Change the accent color:** Find `#EA4B25` (orange) in the style block and replace it with your brand color. Every border, heading, and highlight changes at once.

**Add your logo:** Insert an `<img>` tag at the top of the body. Use a direct image URL — not a local file path.

```html
<img src="https://yoursite.com/logo.png" alt="Your Brand" width="160" style="margin-bottom: 16px;">
```

**Remove a platform section:** If your Claude prompt only outputs two platforms, just delete the `<div class="section">` block for the one you don't use.

**Add a reply-to note:** Put a short instruction at the top so the recipient knows what to do with the email.

```html
<p style="color: #888; font-size: 13px;">Review and edit before posting. Reply to this email with any changes.</p>
```

---

## Gmail Node Settings

When you paste this into the Gmail node, make sure these fields are set:

| Field | Value |
|-------|-------|
| Operation | Send |
| To | your-email@gmail.com |
| Subject | `New Post: {{ $json.title }}` |
| Email Type | **HTML** (toggle this on) |
| Message | paste the HTML template here |

---

## Learn More

If you want to go deeper on HTML email: [W3Schools HTML Tutorial](https://www.w3schools.com/html/)

W3Schools has interactive examples you can edit in the browser. Good for learning tags you haven't used before, looking up specific attributes, and testing how styles render.
