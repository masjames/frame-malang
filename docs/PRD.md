# Frame Malang Migration / Flagship Site PRD

## 1. Product Intent

Frame Malang is the first public KALANA case study built through the ANTE Platform. The site should prove that ANTE can turn an existing WordPress business website into a fast, low-maintenance static site without losing search visibility or operational continuity.

The migration target is a lightweight static site deployed on Vercel at:

https://frame-malang.vercel.app

The first release should prioritize practical business value: preserve existing SEO, make the site faster, reduce maintenance burden, and establish a content structure that can later be generated and managed from ANTE Platform output.

Longer term, Frame Malang becomes a flagship reference for:

- KALANA implementation quality.
- ANTE Platform as the site/content generation engine.
- ANTEP membership and support as the monetization layer for ongoing maintenance, content updates, and business tooling.

## 2. Stakeholders

- **Frame Malang owner/operator:** Needs a reliable, fast, easy-to-maintain website that keeps leads and search traffic intact.
- **KALANA team:** Needs a strong first case study that demonstrates migration speed, quality, and business impact.
- **ANTE Platform team:** Needs a real production use case to validate generated static-site output, content schema, and migration workflow.
- **ANTEP team:** Needs a clear path to package maintenance/support as a recurring membership offer.
- **End customers:** Need to quickly understand services, pricing/fit, location, trust signals, and how to contact Frame Malang.

## 3. Migration Goals

### Primary Goals

- Migrate from WordPress to a fast static site.
- Preserve existing SEO value, URLs where practical, metadata, indexed content, and redirects.
- Improve page speed, Core Web Vitals, uptime, and maintenance simplicity.
- Launch first on free infrastructure with no paid dependencies.
- Use the MVP as the first ANTE Platform flagship output.

### Secondary Goals

- Establish a repeatable migration workflow for future KALANA/ANTE clients.
- Create a clean content model that can later be edited or generated from ANTE Platform.
- Prepare a natural ANTEP support/membership hook without making the site feel like a software demo.
- Create measurable before/after evidence for a future case study.

### Non-Goals for MVP

- Full custom CMS build.
- Paid hosting, paid analytics, paid search tools, or paid plugins.
- Complex ecommerce, booking engine, or gated customer portal.
- Full ANTEP membership implementation inside the Frame Malang public site.

## 4. MVP Page and Content Scope

The MVP should include only the pages needed to preserve SEO, communicate the business clearly, and create a stable migration foundation.

### Required Pages

- **Home**
  - Clear business positioning.
  - Primary services summary.
  - Main call to action.
  - Trust signals, location/service area, and contact options.

- **Services**
  - Service categories offered by Frame Malang.
  - Short descriptions optimized for customer intent and search queries.
  - Internal links to contact/CTA sections.

- **Gallery / Portfolio**
  - Selected work examples.
  - Image alt text and captions where useful.
  - Lightweight optimized images.

- **About**
  - Business background.
  - Location and credibility signals.
  - Brand story kept concise and customer-facing.

- **Contact**
  - WhatsApp/contact CTA.
  - Address or service area.
  - Map link if available.
  - Operating hours if available.

- **Blog / Articles Index**
  - Preserve migrated WordPress posts that still have SEO or customer value.
  - Start with a minimal list view.

- **Article Detail**
  - Static markdown-driven article pages.
  - Preserve titles, dates, slugs, headings, images, and metadata where possible.

### Optional MVP Pages

Add only if they already exist in WordPress and have search or customer value:

- FAQ.
- Pricing or estimate guide.
- Specific service landing pages.
- Customer testimonials.

## 5. Information Architecture

Recommended MVP structure:

```text
/
/services/
/gallery/
/about/
/contact/
/posts/
/posts/[slug]/
```

If the current WordPress site has existing indexed URLs, the static site should either:

- Keep the same path, if clean and compatible.
- Or add a permanent redirect from the old path to the new canonical path.

Internal navigation should remain simple:

- Header: Home, Services, Gallery, About, Contact.
- Footer: Contact, location/service area, key services, social links if available.
- Blog index linked from footer or navigation only if articles are important to SEO.

## 6. Content Model

The MVP content model should be simple, file-based, and compatible with future ANTE Platform output.

### Site Settings

```json
{
  "businessName": "Frame Malang",
  "tagline": "",
  "description": "",
  "phone": "",
  "whatsapp": "",
  "email": "",
  "address": "",
  "serviceArea": [],
  "socialLinks": [],
  "seo": {
    "siteTitle": "",
    "siteDescription": "",
    "defaultImage": ""
  }
}
```

### Page Content

Each page should support:

- `title`
- `slug`
- `description`
- `heroTitle`
- `heroSubtitle`
- `sections`
- `cta`
- `seoTitle`
- `seoDescription`
- `canonicalUrl`

### Service Content

Each service should support:

- `name`
- `slug`
- `summary`
- `description`
- `image`
- `altText`
- `keywords`
- `ctaLabel`

### Post Content

Posts should be markdown-first with frontmatter:

```yaml
---
title: ""
slug: ""
date: "YYYY-MM-DD"
description: ""
seoTitle: ""
seoDescription: ""
canonicalUrl: ""
originalUrl: ""
featuredImage: ""
featuredImageAlt: ""
status: "published"
---
```

This keeps the site usable now while making it easy for ANTE Platform to generate or update content later.

## 7. SEO Preservation

SEO preservation is a release blocker, not a nice-to-have.

### Required SEO Work

- Crawl or inventory the current WordPress site before final cutover.
- Export all existing URLs, page titles, meta descriptions, headings, canonical URLs, and image assets.
- Identify indexed or high-value pages using free tools where possible:
  - Google Search Console, if access exists.
  - `site:` search checks.
  - Existing sitemap.
  - WordPress XML export.
- Preserve high-value slugs whenever possible.
- Create `301` redirects for changed URLs.
- Generate `sitemap.xml`.
- Generate `robots.txt`.
- Add canonical URLs.
- Preserve Open Graph metadata for share previews.
- Add structured data where appropriate:
  - `LocalBusiness`
  - `Organization`
  - `BreadcrumbList` for article/detail pages if useful.
- Optimize images with descriptive filenames and alt text.
- Avoid thin replacement pages for existing content with search value.

### Redirect Requirements

Redirect mapping should include:

- Old URL.
- New URL.
- Redirect type.
- Reason.
- Migration status.

Example:

```csv
old_url,new_url,type,status
/old-wordpress-post/,/posts/new-post/,301,ready
```

### SEO Acceptance Targets

- No known high-value WordPress URL returns `404` after launch.
- All MVP pages have unique title and description metadata.
- Sitemap is valid and submitted or ready to submit.
- Canonicals point to the final production domain once domain cutover happens.
- Page content remains indexable without client-side JavaScript dependency.

## 8. ANTEP Membership Hook

The public Frame Malang site should not over-focus on ANTEP. The hook belongs in the operating model and future case study, not as a distraction for Frame Malang customers.

### MVP Hook

- Add an internal note or case-study-ready section in project docs explaining that ongoing updates can be handled through ANTEP support.
- Keep the public customer journey focused on Frame Malang services.
- Optionally include a subtle footer credit later, such as "Built with KALANA", only if approved by the business owner.

### Future ANTEP Offer

Frame Malang can become proof for an ANTEP membership package:

- Static site hosting/deployment support.
- Monthly content updates.
- SEO monitoring.
- Performance checks.
- Backup/export support.
- Small design/content changes.
- Lead/contact flow maintenance.

This should be packaged after MVP validation, not before the site migration is stable.

## 9. Technical Architecture

### Principles

- Free infrastructure first.
- Static output by default.
- Minimal moving parts.
- No paid CMS dependency.
- ANTE Platform output should become the long-term content/source generator.
- The deployed site should remain portable if hosting changes later.

### Current Deployment

- Static Vercel deployment exists:
  - https://frame-malang.vercel.app

### Recommended MVP Architecture

- Static site repository under `projects/frame-malang`.
- File-based content:
  - `data/site.json` for global settings.
  - `content/posts/*.md` for articles.
  - Future `content/pages/*.md` and `content/services/*.json` or equivalent if needed.
- Build output deployable to Vercel static hosting.
- No runtime database for MVP.
- No paid third-party services.

### Future ANTE Platform Architecture

ANTE Platform should eventually generate:

- Site settings.
- Page content.
- Service content.
- Post markdown.
- Image metadata.
- SEO metadata.
- Redirect map.
- Deployment-ready static output.

The static site should treat ANTE-generated files as source-of-truth inputs once that pipeline exists.

## 10. Deployment Path

### MVP Deployment Path

1. Keep the existing Vercel static deployment active.
2. Build the MVP static site locally.
3. Deploy preview to Vercel.
4. Validate content, links, images, SEO metadata, and page speed.
5. Prepare redirect map and sitemap.
6. Run final owner review.
7. Cut over production domain when ready.
8. Submit updated sitemap to Google Search Console if access exists.

### Domain Cutover Requirements

Before pointing the production domain to Vercel:

- All required pages exist.
- Redirects are configured.
- Sitemap and robots files are ready.
- Contact CTA has been tested.
- Old WordPress content has been backed up/exported.
- Rollback option is understood.

## 11. Data and Content Migration Workflow

### Source Inventory

Collect from WordPress:

- Pages.
- Posts.
- Media library assets.
- Menus/navigation.
- Categories/tags.
- SEO metadata from plugins if available.
- Redirects if a redirect plugin is in use.
- Forms/contact destinations.
- Analytics/search console access if available.

### Migration Steps

1. Export WordPress content using native export or scraping/crawling if admin access is unavailable.
2. Build a URL inventory and classify each URL:
   - Keep.
   - Merge.
   - Redirect.
   - Retire.
3. Convert retained pages into the MVP content model.
4. Convert retained posts into markdown with frontmatter.
5. Download and optimize required images.
6. Map old media URLs if they have search/share value.
7. Add metadata and canonical fields.
8. Generate redirect map.
9. Validate all internal links.
10. Compare MVP pages against source pages for missing critical content.

### Content Quality Rules

- Keep content customer-facing and specific.
- Avoid generic filler.
- Preserve useful local search terms such as Malang, service area, and product/service names where accurate.
- Avoid keyword stuffing.
- Use real business details only after verification.

## 12. Acceptance Criteria

### Product Acceptance

- MVP pages are present: Home, Services, Gallery, About, Contact, Blog index, Article detail.
- Main CTA is visible and works on mobile and desktop.
- Site clearly communicates what Frame Malang offers, where it operates, and how to contact.
- Public content is accurate or explicitly marked as placeholder until verified.

### Migration Acceptance

- Existing WordPress content has been inventoried.
- High-value URLs are preserved or redirected.
- Required posts/pages have been migrated.
- No known critical content is missing.
- WordPress backup/export exists before cutover.

### SEO Acceptance

- Every MVP page has unique title and meta description.
- `sitemap.xml` exists.
- `robots.txt` exists.
- Canonical URLs exist.
- Redirect map exists before domain cutover.
- No high-value migrated URL returns `404`.
- LocalBusiness structured data is added if verified business details are available.

### Performance Acceptance

- Site is statically rendered.
- Pages are usable without heavy JavaScript.
- Images are compressed and appropriately sized.
- Lighthouse or equivalent free audit shows strong performance on the main pages.

### Technical Acceptance

- Site deploys successfully to Vercel.
- Content can be updated from files.
- Build/deploy process is documented in the project README or deployment notes.
- Architecture does not require paid infrastructure for MVP.
- ANTE Platform can later generate the same content structure without a rewrite.

## 13. Risks and Mitigations

### SEO Traffic Loss

- **Risk:** URL changes, missing metadata, or missing redirects reduce organic traffic.
- **Mitigation:** Inventory URLs before launch, preserve slugs, create redirects, validate sitemap, monitor Search Console after cutover.

### Missing WordPress Access

- **Risk:** Admin access or plugin metadata is unavailable.
- **Mitigation:** Use public crawl, sitemap, page source, and manual extraction as fallback.

### Content Inaccuracy

- **Risk:** Migrated or generated copy misrepresents Frame Malang.
- **Mitigation:** Owner review before cutover; mark unknown details as pending verification.

### Image Quality or Licensing Issues

- **Risk:** Migrated images are too large, broken, or not approved for reuse.
- **Mitigation:** Use only existing business-owned assets or approved replacements; optimize before deployment.

### Free Infrastructure Limits

- **Risk:** Free-tier limits or deployment constraints affect reliability.
- **Mitigation:** Keep site static, lightweight, and portable; avoid runtime services for MVP.

### ANTE Platform Dependency Too Early

- **Risk:** Waiting for the full ANTE pipeline delays the migration.
- **Mitigation:** Use file-based content now; align schema with future ANTE output.

### Scope Creep

- **Risk:** Adding CMS, membership, booking, or complex automation delays MVP.
- **Mitigation:** Keep MVP to migration, speed, SEO, and core business pages.

## 14. Milestones

### Milestone 1: Discovery and Inventory

- Confirm current WordPress URL.
- Export or crawl existing content.
- Create URL inventory.
- Identify must-preserve pages/posts.
- Confirm business contact details and service scope.

### Milestone 2: MVP Content Structure

- Finalize IA.
- Define site settings.
- Create core page content.
- Convert first retained posts to markdown.
- Prepare image list and alt text.

### Milestone 3: Static Site MVP

- Implement static pages.
- Add navigation and footer.
- Add responsive layout.
- Add contact CTA.
- Deploy to Vercel preview/current static deployment.

### Milestone 4: SEO Migration Readiness

- Add metadata.
- Add sitemap and robots.
- Add structured data where verified.
- Create redirect map.
- Validate internal links.

### Milestone 5: Review and Cutover

- Owner/content review.
- Performance audit.
- Mobile QA.
- Domain cutover plan.
- Production launch.
- Post-launch SEO monitoring.

### Milestone 6: Case Study and ANTEP Packaging

- Document before/after speed and maintenance improvements.
- Capture migration workflow as a repeatable KALANA process.
- Define ANTEP support package based on actual maintenance needs.

## 15. Next Tasks

1. Confirm the current live WordPress URL and production domain.
2. Crawl the existing WordPress site and export URL inventory.
3. Check whether Google Search Console access exists.
4. Identify top pages/posts to preserve for SEO.
5. Verify Frame Malang business details:
   - Services.
   - Contact number.
   - WhatsApp link.
   - Address/service area.
   - Operating hours.
   - Social links.
6. Decide canonical MVP URL structure.
7. Create redirect map draft.
8. Expand `data/site.json` with verified site settings.
9. Convert priority WordPress posts into markdown.
10. Add page metadata, sitemap, robots, and structured data.
11. Run performance and link checks on the Vercel deployment.
12. Prepare a short case-study outline for KALANA/ANTE after MVP launch.
