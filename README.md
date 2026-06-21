# Serverless Agent — Live Cost Calculator

An interactive cost calculator for a low-cost, 100% serverless AWS Bedrock agent architecture. Adjust monthly interaction volume, model mix, token usage, and infrastructure settings to see live AWS cost estimates — and how they compare to a traditional always-on architecture.

**Live demo:** _(add your deployed URL here)_

![Preview](og-image.png)

## What it does

The calculator models real AWS pricing across the full stack a Bedrock agent needs to run: API Gateway, Lambda, Bedrock model inference (Nova Micro / Claude Haiku / Claude Sonnet), Bedrock Knowledge Base, Aurora Serverless v2 + pgvector, DynamoDB, S3, messaging (SQS/SNS/EventBridge), Step Functions, CloudWatch, Secrets Manager, and WAF.

Every figure recalculates live as you move the sliders — there are no hardcoded cost ranges. Four presets (Pilot, Production, Scale, Enterprise) jump to realistic volume profiles, and a side-by-side comparison shows what the same workload would cost on a traditional always-on architecture (OpenSearch, ElastiCache, RDS, six separate agents) for context.

## Features

- Live recalculation across 15 AWS services as inputs change
- Quick-scenario presets for different deployment sizes
- Optimised-vs-legacy cost comparison with savings percentage
- Cost composition breakdown by category (entry/security, compute, AI models, data, observability)
- Per-service cost table with relative-share bars
- Dark, data-dense visual style with no build step required

## Files

| File | Purpose |
|---|---|
| `index.html` | The calculator — self-contained HTML/CSS/JS, no dependencies to install |
| `og-image.png` | Social share preview image (1200×630) used by the Open Graph tags |
| `og-image.svg` | Source vector for the preview image |
| `LICENSE` | MIT license |

## Running locally

No build step — just open the file:

```
open index.html
```

or serve it with any static server, e.g.:

```
python3 -m http.server 8000
```

## Deploying

### Netlify (fastest, no account needed for a first link)
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the project folder onto the page
3. Netlify returns a live URL immediately (e.g. `https://random-name-123.netlify.app`)
4. Optional: create a free account to keep the link permanent and pick a custom subdomain

### GitHub Pages
1. Push this folder to a GitHub repository
2. **Settings → Pages → Source → Deploy from a branch → `main` / `(root)`**
3. Live within a couple of minutes at `https://<username>.github.io/<repo-name>/`

## Customizing the pricing model

All pricing constants live in a single `PRICE` object near the top of the `<script>` block in `index.html` — token rates, per-request costs, ACU-hour pricing, and so on. Update those values to reflect new AWS pricing or a different region, and every downstream calculation updates automatically.

## License

MIT — see [`LICENSE`](LICENSE).

---
Developed by **Gaurav Kumar**
