follow this shit to make a post

---

## Creating a New Post

1. Create a new `.md` file in the `_posts/` folder
2. Name it using the format: `YYYY-MM-DD-your-post-title-here.md`
3. Add the required front matter (see below)
4. Write your content in Markdown
5. Run `bundle exec jekyll build` to verify, or `bundle exec jekyll serve` to preview

The post will automatically appear on the home page's blog grid and get its own page at:
```
yourdomain.com/your-post-title-here/
```

---

## Front Matter Reference

Every post **must** start with a YAML front matter block between `---` fences. Here's every available field:

```yaml
---
layout: post              # REQUIRED — always "post"
title: "Your Post Title"  # REQUIRED — appears as the page heading and in the card
subtitle: "A longer description that appears below the title on the post page."  # Optional but recommended
date: 2026-03-04          # REQUIRED — format: YYYY-MM-DD
category: GRC & Law       # Optional — single category shown as a badge on the card
tags: [GRC, Compliance, Cyber Law]  # Optional — array of tags shown below the card
readtime: "8 min read"    # Optional — shown next to the date
toc:                       # Optional — generates a "In this article" box
  - id: section-id         #   Must match the {: #section-id} on the heading
    title: Section Title   #   Display text in the TOC
  - id: another-section
    title: Another Section
---
```

### Field Details

| Field      | Required | Type             | Description                                                                 |
|------------|----------|------------------|-----------------------------------------------------------------------------|
| `layout`   | ✅       | String           | Always `post`                                                               |
| `title`    | ✅       | String           | Post title. Wrap in quotes if it contains colons or special characters.      |
| `subtitle` | ❌       | String           | Secondary description shown under the title on the post page.               |
| `date`     | ✅       | Date             | `YYYY-MM-DD` format. Controls sort order and display date.                  |
| `category` | ❌       | String           | Single category. Shown as a coral badge on the post card.                   |
| `tags`     | ❌       | Array of Strings | Shown as small pill badges. Use `[Tag1, Tag2, Tag3]` syntax.               |
| `readtime` | ❌       | String           | e.g. `"8 min read"`. Shown next to the publish date.                        |
| `toc`      | ❌       | Array of Objects | Each item needs `id` (anchor) and `title` (display text).                   |

---

## Writing the Body

After the front matter `---`, write your post in standard Markdown. The first paragraph becomes the **excerpt** shown on the blog card on the home page (auto-truncated to ~25 words).

### Section Headings with Anchors (for TOC)

If you're using the `toc` front matter, you need to add anchor IDs to your headings:

```markdown
## Your Section Title
{: #your-section-id}
```

The `#your-section-id` must match the `id` in your `toc` front matter exactly.

---

## Formatting Guide

Here's everything you can use in the post body and how it renders:

### Headings

```markdown
## Main Section Heading        ← Use for major sections (renders with top border)
### Sub-section Heading        ← Use for subsections
#### Minor Heading             ← Rarely needed
```

> **Note:** Don't use `# H1` in the body — the post title is already an H1.

### Paragraphs

Just write normally with a blank line between paragraphs:

```markdown
This is the first paragraph.

This is the second paragraph.
```

### Bold & Italic

```markdown
**Bold text** for emphasis
*Italic text* for softer emphasis
***Bold italic*** for maximum emphasis
```

### Lists

**Bullet list:**
```markdown
- First item
- Second item
- Third item with **bold** inside
```

**Numbered list:**
```markdown
1. First step
2. Second step
3. Third step
```

**Nested list:**
```markdown
- Parent item
  - Child item
  - Another child
- Another parent
```

### Blockquotes

Renders with a coral left border and pink background:

```markdown
> "Security without governance is like a ship without a rudder — you might stay afloat, but you'll never reach your destination."
```

### Links

```markdown
[Link text](https://example.com)
```

Links in posts render in the coral/pink accent color with an underline.

### Inline Code

```markdown
Use `backticks` for inline code, variable names like `NIST_CSF`, or commands like `nmap`.
```

Renders with a light pink background and coral text.

### Code Blocks

````markdown
```
Multi-line code blocks
render with a dark background
and monospace font
```
````

For syntax-highlighted code, specify the language:

````markdown
```python
def assess_risk(asset, threat, vulnerability):
    return asset * threat * vulnerability
```
````

### Bold Terms in Lists (Common Pattern)

This is used heavily in existing posts for emphasis:

```markdown
- **Governance** establishes the policies and procedures that guide security
- **Risk Management** identifies and prioritizes threats
- **Compliance** ensures regulatory obligations are met
```

### Horizontal Rules

```markdown
---
```

Creates a visual separator between sections.

### Images

```markdown
![Alt text description](/assets/your-image.jpg)
```

Place images in the `assets/` folder.

---

## Categories & Tags

### Current Categories in Use

| Category      | Used For                                      |
|---------------|-----------------------------------------------|
| `GRC & Law`   | Governance, risk, compliance, and legal topics |
| `Competition`  | CCDC, CPTC, and other cyber competitions      |
| `Cyber Law`   | Legal frameworks, regulations, criminal law    |

You can create new categories — they'll automatically work. Just pick a short, descriptive name.

### Current Tags in Use

`GRC` · `Compliance` · `Cyber Law` · `Security Policy` · `CCDC` · `Criminal Law` · `Policy` · `Team`

Tags are flexible — add whatever is relevant. Keep them concise (1-3 words each).

---

## File Naming

```
_posts/YYYY-MM-DD-title-with-dashes.md
```

**Rules:**
- Date must be today or in the past (future dates won't publish)
- Use lowercase
- Replace spaces with hyphens
- Remove special characters
- Keep it readable but concise

**Examples:**
```
_posts/2026-03-04-understanding-grc-makes-you-a-better-cybersecurity-professional.md
_posts/2026-02-15-what-i-learned-competing-at-national-ccdc.md
_posts/2026-01-20-why-every-cybersecurity-professional-needs-to-understand-cyber-law.md
```

The filename (minus the date) becomes the URL slug:
```
yourdomain.com/understanding-grc-makes-you-a-better-cybersecurity-professional/
```

---

## Images & Media

- Place all images in the `assets/` folder
- Reference them with: `{{ '/assets/filename.jpg' | relative_url }}`
- Or in plain Markdown: `![Alt text](/assets/filename.jpg)`
- Supported formats: `.jpg`, `.png`, `.gif`, `.svg`, `.webp`
- The site headshot is at `assets/headshot.jpg` (also used as favicon)

---

## Quick-Start Template

Copy this entire block into a new file in `_posts/` to get stuff:

```markdown
---
layout: post
title: "Your Post Title Here"
subtitle: "A brief description of what this post covers."
date: 2026-XX-XX
category: GRC & Law
tags: [Tag1, Tag2, Tag3]
readtime: "X min read"
toc:
  - id: first-section
    title: First Section
  - id: second-section
    title: Second Section
  - id: conclusion
    title: Conclusion
---

Your opening paragraph goes here. This first paragraph is what shows up as the
preview text on the blog card on the home page, so make it count — hook the
reader in 1-2 sentences.

## First Section
{: #first-section}

Content for the first section...

## Second Section
{: #second-section}

Content for the second section...

## Conclusion
{: #conclusion}

Wrap up your thoughts here.
```
