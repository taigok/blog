# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

### Development
```bash
npm run dev      # Start development server on http://localhost:3000
npm run build    # Build for production
npm run start    # Start production server
```

### Adding a new blog post
Create a new `.mdx` file in `/app/blog/posts/` with the following format:
```mdx
---
title: 'Your Post Title'
publishedAt: 2025-05-31
---

Your content here...
```

The filename (without .mdx) becomes the URL slug: `filename.mdx` → `/blog/filename`

## Architecture

This is a Next.js 14+ blog using App Router and static site generation.

### Key architectural decisions:
- **MDX for content**: Blog posts are written in MDX files stored in `/app/blog/posts/`
- **Static generation**: All pages are statically generated at build time for optimal performance
- **Dynamic routing**: Blog posts use `[slug]` dynamic routing pattern
- **Server Components**: Leverages React Server Components for better performance

### Content rendering flow:
1. MDX files are parsed from `/app/blog/posts/` using Node.js file system
2. Posts are rendered using `next-mdx-remote` with custom components defined in `/app/components/mdx.tsx`
3. Metadata (title, publishedAt) is extracted from frontmatter
4. Posts are sorted by date and displayed on the blog index

### SEO and metadata:
- Each page generates OpenGraph images dynamically via `/app/og/route.tsx`
- Structured data (JSON-LD) is added for blog posts
- Sitemap and robots.txt are auto-generated
- RSS feed available at `/rss`

### Styling:
- Tailwind CSS v4 (alpha) with PostCSS
- Global styles in `/app/global.css`
- Typography styles optimized for readability

## Important notes

- No test framework is configured
- Uses npm as package manager (despite pnpm-lock.yaml presence)
- The project is primarily in Japanese with some English content
- Analytics are integrated via Vercel Analytics and Speed Insights

## Blog post style guide

記事は以下の統一されたスタイルで書く：

### 構造
1. **導入部**: `[参考記事](URL) より、〜についてまとめる。` で始める（参考記事がある場合）
2. **見出し**: 
   - `## トピックについて`
   - `### どんな〜か？` （疑問形の小見出し）
   - `## 具体的な手順` または `## なぜ〜か？`
   - `## まとめ`

### 文体
- 「である」調で統一
- 簡潔で要点を押さえた説明
- 技術用語は必要に応じて英語併記（例：overkill（過剰））
- 箇条書きを活用
- まとめは1-2文で端的に