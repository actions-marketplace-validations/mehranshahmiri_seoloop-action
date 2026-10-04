<p align="center"><img src="https://seoloop.in/logo.png" alt="SEO Loop" width="260"></p>

# SEO Loop audit (GitHub Action)

Audit a URL with [SEO Loop](https://seoloop.in), write the report to the job summary, and fail the job when the SEO score drops below a minimum.

```yaml
- uses: mehranshahmiri/seoloop-action@v1
  with:
    url: https://staging.example.com
    min-score: 80
```

## Inputs

| Input | Default | Description |
|---|---|---|
| `url` | required | Public URL or domain to audit |
| `min-score` | `0` | Fail the job below this score (0 disables) |
| `only` | | Comma-separated categories (`seo`, `performance`, `security`, `crawlability`) or check ids to include |
| `skip` | | Categories or check ids to exclude, e.g. `sitemap,hsts` |
| `server` | `https://seoloop.in` | Use your own [self-hosted instance](https://github.com/mehranshahmiri/seoloop#self-host) |

## Outputs

`score` (0-100) and `grade` (A-F).

## Notes

- The URL must be reachable from the public internet (use a deployed preview or staging site, not `localhost`).
- Audits are rate limited per IP; the action retries once on HTTP 429.
- Source for the service: https://github.com/mehranshahmiri/seoloop (MIT).
