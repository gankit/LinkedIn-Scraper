# LinkedIn Saved Posts Scraper

A Python tool to export your LinkedIn saved posts to markdown files.

## Setup

1. **Install dependencies:**
   \`\`\`bash
   pip install -r requirements.txt
   \`\`\`

2. **Install Playwright browsers:**
   \`\`\`bash
   playwright install chromium
   \`\`\`

## Usage

Run the script:
\`\`\`bash
python linkedin_saved_posts_scraper.py
\`\`\`

### What happens:
1. A browser window opens and navigates to LinkedIn
2. If not logged in, you'll need to log in manually
3. The script waits for you to complete login
4. It scrolls through your saved posts to load them all
5. Extracts author names, post content, and any links shared in each post
6. Creates a folder `saved_posts/` with:
   - Individual `.md` files for each post (including a `## Links` section)
   - A `README.md` index file
   - A `links.md` file listing every link found across all posts

## Output Structure

\`\`\`
saved_posts/
├── README.md              # Index of all posts
├── links.md               # All links extracted from every post
├── 001-John-Doe.md        # Individual post files
├── 002-Jane-Smith.md
└── ...
\`\`\`

## Links

Each post often shares external articles, tools, or resources. The scraper
collects these from:

- Anchor tags in the post (unwrapping LinkedIn `/redir/` safety-redirects)
- `lnkd.in` short links
- Plain-text URLs in the post body

LinkedIn navigation links (profiles, hashtags, the post's own permalink) are
filtered out. Extracted links appear in each post's `## Links` section, in the
consolidated `links.md`, and in the HTML viewer (link count on each card plus a
clickable list in the post modal).

## Notes

- LinkedIn requires authentication, so the browser opens visibly
- The script handles various LinkedIn page layouts
- Posts are numbered in the order they appear
- If no posts are found, try scrolling manually in the browser

## Troubleshooting

- **Login issues:** Make sure you complete the login process in the browser
- **No posts found:** LinkedIn may have changed their page structure
- **Timeout errors:** Increase wait times in the script
