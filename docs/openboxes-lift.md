# OpenBoxes Lift — context for the marketing site

Reference notes for writing/maintaining OpenBoxes **Lift** content on this site.
Lift is the commercial, fully managed SaaS version of OpenBoxes. Its source lives
in the peer repo `../lift` (a separate project). **That repo and `openboxes.cloud/pricing`
are the source of truth** — re-verify prices/tiers there before quoting them here,
since the soft-launch offer and tier availability change.

_Last synced from `../lift`: 2026-06 (soft-launch / pilot phase)._

## What Lift is

Fully managed cloud hosting for OpenBoxes: provisioning, SSL, backups, monitoring,
security patches, and upgrades are all handled for the customer. Instances run at
`{subdomain}.openboxes.cloud`. Positioned for healthcare orgs, NGOs, and government
health programs — especially **organizations that lack the developer/IT resources to
self-host** and want a turnkey, supported system.

Headline value props: fast setup (minutes, not months), fully managed, included
support, REST API access, automatic encrypted backups, tenant-isolated data,
guaranteed uptime SLAs.

## Canonical URLs

| Purpose | URL |
|---|---|
| Marketing site | https://openboxes.cloud |
| Pricing | https://openboxes.cloud/pricing |
| Demo (resets hourly) | https://openboxes.cloud/demo |
| Customer app/portal | https://app.openboxes.cloud |

## Plans / tiers

Three tiers: **Shared**, **Dedicated**, **Enterprise**. At soft launch only Shared is
self-serve; Dedicated and Enterprise are waitlisted.

| | Shared | Dedicated | Enterprise |
|---|---|---|---|
| Price (regular) | $149/mo | $899/mo | Custom |
| Price (founding, 50% off) | **$74.50/mo** (≈ the **$75** we show) | — | — |
| Annual (regular) | $119/mo billed annually | $719/mo billed annually | Custom |
| Users | up to 10 | up to 50 | custom |
| Storage | 10 GB | 100 GB | custom |
| API rate limit | 1k/hr | 25k/hr | custom |
| Infrastructure | shared multi-tenant (schema-isolated) | dedicated instance | dedicated cluster |
| Uptime SLA | 99.0% | 99.5% | 99.9% |
| Backup retention | 30 days | 60 days | 90+ days |
| Support | live chat + community | priority email | dedicated account manager, 24/7 phone + chat |
| SSO / Audit logs | — | included | included |

> The founding-member price (FOUNDING50, 50% off for 24 cycles, through 2026-12-31)
> is why the pricing **card** advertises "Starting at $75/mo." Keep the card and the
> support matrix consistent with whatever `openboxes.cloud/pricing` currently shows.

### Support response-time SLAs (used in the support matrix)

| Priority | Shared | Dedicated | Enterprise |
|---|---|---|---|
| High | < 48h | < 4h | < 15 min |
| Medium | < 72h | < 8h | < 1h |
| Low | < 1 week | < 48h | < 4h |

## How this maps onto the /pricing page

- **Hosting packages** (`layouts/partials/pricing/packages.html`): three cards —
  Community Edition (free, DIY self-host), Self-Hosted (DigitalOcean), and
  **OpenBoxes Lift** (highlighted "Most Popular", from $75/mo, Configuration + Data
  Migration + Dedicated Support included). The Lift CTA → `openboxes.cloud`.
- **Support matrix** (`layouts/partials/pricing/support.html`): four columns —
  Community (self-hosted) + the three Lift tiers (Shared / Dedicated / Enterprise).
  All three Lift CTAs → `openboxes.cloud/pricing`.
- **Add-on Services** (`layouts/partials/pricing/services.html`): à-la-carte help
  for **self-hosted Community Edition** users; Lift customers don't need these.
- **FAQs** (`data/pricingfaqs/*.yml`): position Lift as the option for orgs without
  developer resources or the ability to self-host.
