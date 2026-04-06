# englishcollege

Public repository hosting auto-generated SEO and LLM context files for [englishcollege.com](https://www.englishcollege.com).

## Files

| File | Description | Updated |
|------|-------------|---------|
| `sitemap.xml` | Merged multilingual sitemap (EN + 8 languages, ~655 URLs) | Every 12 hours |
| `llms.txt` | LLM-friendly context extracted from sitemap | Every 12 hours |

## Public URLs

- **Sitemap**: `https://cagdasunal.github.io/englishcollege/sitemap.xml`
- **LLMs.txt**: `https://cagdasunal.github.io/englishcollege/llms.txt`
- **Raw sitemap**: `https://raw.githubusercontent.com/cagdasunal/englishcollege/main/sitemap.xml`
- **Raw llms.txt**: `https://raw.githubusercontent.com/cagdasunal/englishcollege/main/llms.txt`

## How It Works

A GitHub Actions workflow runs every 12 hours:

1. **Sitemap generation** (`tools/generate_master_sitemap.py`): Fetches 9 sitemaps (1 primary + 8 regional languages), deduplicates translated blog posts, and merges into one `sitemap.xml`.

2. **LLMs.txt generation** (`tools/generate_llms.sh`): Reads the sitemap and uses the `llmstxt` NPM package to extract page content into a structured context file for LLMs.

3. **Auto-commit**: If either file changed, the workflow commits and pushes. GitHub Pages serves the updated files.

## Manual Trigger

Go to **Actions** tab > **Update Sitemap & LLMs.txt** > **Run workflow**.

## Adding More Sites

Edit `tools/sites.json` to add entries. Each site needs:
- `id`: Unique identifier
- `name`: Display name
- `description`: One-line description
- `sitemap_url`: URL to the site's sitemap.xml
- `output`: Output file path (relative to repo root)
