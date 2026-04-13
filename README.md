# englishcollege

Public repository hosting auto-generated SEO files for [englishcollege.com](https://www.englishcollege.com).

## Files

| File | Description | Updated |
|------|-------------|---------|
| `sitemap.xml` | Filtered multilingual sitemap (EN + 8 languages, ~696 URLs) | Every 6 hours + on new posts |
| `llms.txt` | LLM-friendly context extracted from sitemap | Every 6 hours |
| `weglot.csv` | Weglot exclusion CSV for dashboard import | Every 15 minutes |

## Public URLs

- **Sitemap**: `https://sitemap.englishcollege.com/sitemap.xml`
- **LLMs.txt**: `https://sitemap.englishcollege.com/llms.txt`
- **Weglot CSV**: `https://sitemap.englishcollege.com/weglot.csv`

## Automation

### Sitemap & LLMs.txt (`update-sitemap-llms.yml`)
Runs every 6 hours. Generates `sitemap.xml` from 9 sitemaps (EN + 8 regional), filters ghost translations and category pages, then generates `llms.txt` from the filtered sitemap.

### Weglot Exclusion Sync (`weglot-sync.yml`)
Runs every 15 minutes. Detects new published blog posts in Webflow CMS, generates `weglot.csv` for Weglot dashboard import, and regenerates the sitemap. After importing the CSV, next run auto-confirms and clears. See `tools/weglot/README.md` for details.

## Manual Trigger

Go to **Actions** tab > select workflow > **Run workflow**.
