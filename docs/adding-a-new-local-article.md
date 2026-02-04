# Adding a New Local Article

## 1. Create the file

Create an `.mdx` file in `data/blog/`:

```
data/blog/my-post-title.mdx
```

The filename becomes the URL: `/blog/my-post-title`

For a series, use folders:

```
data/blog/series-name/part-1.mdx  ->  /blog/series-name/part-1
```

## 2. Frontmatter template

```yaml
---
title: 'Your Post Title'
date: '2026-02-04'
tags: ['ai', 'web-dev']
draft: false
summary: 'Short description for listings and SEO'
images: ['/static/images/your-post/banner.png']
layout: PostLayout
---
```

| Field | Required | Notes |
|---|---|---|
| `title` | Yes | |
| `date` | Yes | `YYYY-MM-DD` |
| `tags` | No | Array of strings |
| `draft` | No | `true` = hidden in production, visible in dev |
| `summary` | No | Used in post listings and SEO |
| `images` | No | First image used as social sharing card |
| `layout` | No | `PostLayout` (default), `PostSimple`, or `PostBanner` |
| `lastmod` | No | Last modified date |
| `authors` | No | Defaults to `['default']` (you) |
| `canonicalUrl` | No | For cross-posted content |

## 3. Images

Place images in `public/static/images/` (organize by post):

```
public/static/images/my-post/
  screenshot.png
  diagram.png
```

Use in your article:

```markdown
![Alt text](/static/images/my-post/screenshot.png)
```

Or with the Next.js Image component for better performance:

```mdx
import Image from '@/components/Image'

<Image src="/static/images/my-post/screenshot.png" alt="Description" width={800} height={400} />
```

## 4. YouTube videos

```mdx
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/VIDEO_ID"
  title="Video title"
  allowFullScreen
/>
```

## 5. Run locally

```bash
yarn dev
```

Open `http://localhost:3000` — new posts appear automatically.
