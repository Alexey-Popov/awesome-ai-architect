---
title: "Data Scraping Guidelines"
summary: "Best practices for respecting robots.txt, throttling requests, and honoring content licensing when collecting data"
---

# Data Scraping Guidelines

> Collect data responsibly by honoring site rules, limiting request rates, and verifying licensing terms.

![data acquisition and web scraping](/img/data-acquisition-and-web-scrapping.png)

## TL;DR
- **robots.txt** files describe which parts of a site crawlers may access.
- **Throttling** your requests prevents service disruption and avoids getting blocked.
- **Content licensing** determines how you can legally use the data you gather.

## Quickstart (Do this now)
1. Review the target site's `robots.txt` before scraping.
2. Implement delays or rate limits between requests.
3. Check the content's license to confirm your intended use is permitted.

## Key Concepts
### robots.txt
`robots.txt` is a publicly accessible file where site owners state which paths crawlers may or may not visit. Always obey these directives before fetching data.

### Throttling
Throttling controls how frequently your scraper makes requests. Use sleep intervals or concurrency limits to reduce load on the host and stay within acceptable usage.

### Content Licensing
Content is typically covered by copyright or specific licenses. Verify that the license allows scraping, storage, and redistribution for your project.

## Next Steps
- Explore storage options in [Databases for AI](databases-for-ai.md)
