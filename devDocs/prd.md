# PRD: MAS Precision Parts LinkedIn Content System

## Summary
Build a repeatable LinkedIn content system for MAS Precision Parts that captures shop-floor expertise, improves brand trust, and generates qualified inbound leads without heavy daily effort. The system should turn real shop activity into consistent, high-quality posts.

## Company Snapshot (from website content)
- Location: Woodbridge, Ontario, Canada (GTA).
- Since: 1989.
- Core: CNC machining, custom metal fabrication, rapid prototyping.
- Services: CNC milling & turning, surface & jig grinding, wire EDM, reverse engineering, rapid prototyping, custom tooling/jigs/fixtures, welding, bending, anodizing, heat treating.
- Capabilities: tight tolerances to ±0.0001", high-mix low-volume (HMLV), rush 24–72 hour turnaround.
- Materials: tool steel, carbon steel, stainless steel, aluminum, copper/brass, engineering plastics.
- Industries: automotive, aerospace, medical devices, industrial automation, food & beverage, energy.

## Goals
- Publish 3–5 posts per week that reflect MAS Precision Parts capabilities and culture.
- Increase profile visits, follower growth, and inbound inquiries from target buyers.
- Create a simple workflow that the team can run in <2 hours/week.

## Non-Goals
- No paid ads or automated DMs in this phase.
- No scraping of private data or bypassing access controls.
- Not aiming to replace sales outreach; this is brand + inbound support.

## Audience
Primary:
- Procurement managers
- Engineers
- Plant managers
- OEM and contract manufacturing buyers

Secondary:
- Local hiring candidates
- Industry partners

## Success Metrics (first 90 days)
- Post cadence: 3+ posts/week
- Follower growth: +10% or more
- Engagement rate: +2% average
- Inbound inquiries: 3–5 qualified leads/month attributed to LinkedIn

## Voice and Brand
- Precise, confident, helpful, practical.
- Emphasize quality, reliability, and process discipline.
- Use real shop photos, tolerances, materials, process steps.

## Inputs (content sources)
- Shop floor photos/videos (with customer-sensitive info removed)
- Part stories (what it is, material, tolerance, process)
- Process highlights (fixturing, inspection, deburring, coatings)
- Tooling upgrades, maintenance wins, QC improvements
- Employee spotlights and safety wins
- Customer value stories (anonymized)
- Public LinkedIn creator posts for benchmarking (public content only, optional)

## Asset-First Rule
- Posts should be drafted from pre-captured assets and notes in the content tracker.
- The LLM generates copy; it does not invent technical details.
- Exceptions: text-only posts (tips, explainers, procurement guidance) must be tagged as "no asset" and avoid specific claims.

## Technical Objectives
- Create a repeatable pipeline that turns raw inputs into approved LinkedIn posts.
- Maintain a structured content database for analysis and reuse.
- Support automated benchmarking of public LinkedIn posts to extract patterns.
- Enable prompt-driven post creation with QA checks and compliance gates.

## System Architecture (high level)
1) Source capture (shop + public benchmarks)
2) Ingestion and normalization (Apify + manual input)
3) Analysis layer (Claude + spreadsheets)
4) Content generation (Claude skills + templates)
5) Human review and approval (internal)
6) Scheduling and publishing (LinkedIn)
7) Measurement and feedback loop

## System Components (tools + role)
### 1) Source Capture
- Shop assets: photos, short clips, job notes, inspection images.
- Public benchmark data: Top creators in machining/manufacturing on LinkedIn.

### 2) Data Ingestion (Apify)
- Tool: Apify LinkedIn Post Search Scraper.
- Scope: public posts from a curated list of 10–20 relevant creators.
- Config: cookies, user agent, source URLs, rate limits.
- Output: JSON or CSV of post text, media type, engagement, date, author.

### 3) Analysis (Claude)
- Upload scraped dataset (CSV/JSON) to Claude.
- Ask for pattern analysis (hooks, length, CTA usage, formatting, media type).
- Output: pattern report and ranked post examples.

### 4) Generation (Claude skills)
Create two internal skills:
- `linkedin-hook-writer`: generates hooks based on validated formulas.
- `linkedin-post-writer`: generates full posts from MAS templates and facts.

Optional third skill:
- `brand-voice-skill`: rewrites posts to match MAS tone and constraints.

### 5) Review + Publish
- Human review for accuracy and NDA compliance.
- Schedule via LinkedIn native scheduler or Buffer.
- Track results by pillar and template.

## Data Model (minimum)
Store in Google Sheet or Airtable:
- Post ID
- Date
- Pillar
- Template
- Hook formula
- Topic
- CTA type
- Media type
- Word/character count
- Source asset link
- Status (draft/review/approved/published)
- Performance metrics (impressions, reactions, comments, CTR)

## Technical Workflow (step-by-step)
Step 1) Benchmark setup (monthly or quarterly)
- Build a list of 10–20 public LinkedIn creators in machining/manufacturing.
- Run Apify scraper with 900–1500 posts total.
- Export dataset to CSV.

Step 2) Pattern analysis
- Upload CSV to Claude with analysis prompt.
- Produce a pattern report: media mix, length, structure, CTA usage.
- Extract top hooks and top post templates.
 - Save summary stats and examples in the analysis report template.

Step 3) Template + prompt bank
- Convert insights into 6–8 MAS-specific templates.
- Save prompts and examples in `devDocs/prompts.md`.

Step 4) Weekly content intake
- 30–45 min capture of shop highlights.
- Add to content tracker with asset links and notes.

Step 5) Draft generation
- Run `linkedin-hook-writer` for 3–5 hooks per topic.
- Run `linkedin-post-writer` for full posts.
- Apply `brand-voice-skill` for final polish.

Step 6) QA + compliance
- Check NDA, accuracy, tolerances, materials, and lead times.
- Ensure no customer names, drawings, or proprietary parts are exposed.

Step 7) Publish + measure
- Post 3–5x/week.
- Track results and refine templates monthly.

## Content Pillars
1) Capability and process
2) Quality and inspection
3) Lead time and responsiveness
4) Materials and tolerances
5) Problem solving and engineering support
6) Culture, hiring, and community
7) Industry-specific proof (automotive, aerospace, medical devices, industrial automation, food & beverage, energy)

## System Workflow
1) Weekly intake
   - 30 min capture of shop highlights, photos, and quick notes
2) Pattern-based drafting
   - Use fixed templates for 6 post types
3) Review and compliance
   - Remove customer-sensitive data and confirm claims
4) Publish and engage
   - Post during business hours; reply to comments within 24 hours
5) Measure and iterate
   - Track engagement by pillar, refine templates monthly

## Post Templates (initial set)
- Before/After problem solving
- Process walkthrough (step-by-step)
- Capability spotlight (material/tolerance)
- Quality control insight
- Behind-the-scenes culture
- Quick tip for engineers/procurement

## Tools and Assets
- Content tracker (Google Sheet or Airtable)
- Asset library (photos, short clips)
- Template bank (md file)
- Prompt library (for drafting)
- Monthly report template
- Company fact sheet (validated from the website)
 - Apify actor configuration (cookies, user-agent, rate limits)
 - Claude analysis prompt + report template
 - Claude skills: hook writer, post writer, brand voice
 - Example output library (best-performing posts + annotated breakdowns)

## Prompt Requirements (starter)
- Inputs: topic, pillar, template, target reader, asset description, CTA.
- Outputs: 1 hook + full post (900–1,700 characters).
- Formatting: short paragraphs, optional arrows (→, ↳), clear CTA.
- Constraints: no customer names, no proprietary details, no overclaims.

## Compliance and Risk
- No sharing of customer names, drawings, or proprietary parts.
- Verify claims (tolerances, materials, lead time) before posting.
- Follow LinkedIn platform policies and internal NDA requirements.
 - Apify scraping limited to public content and compliant usage.

## Phases and Timeline
Phase 1 (Week 1-2):
- Build template bank and prompts
- Capture 20+ asset items
- Publish 6-8 posts

Phase 2 (Week 3-6):
- Establish cadence
- A/B test 2 hook styles
- Create 2 case-study style posts

Phase 3 (Week 7-12):
- Refine best-performing pillars
- Create a quarterly recap post
- Document SOP for repeatability

## Deliverables
- `devDocs/prd.md` (this document)
- `devDocs/templates.md` (post templates)
- `devDocs/prompts.md` (prompt library)
- `devDocs/content_tracker.csv` (starter tracker)
- `devDocs/sop.md` (step-by-step operating procedure)
 - `devDocs/analysis_report_template.md` (pattern report format)
 - `devDocs/apify_config.md` (scraper config and inputs)
 - `devDocs/skills_spec.md` (Claude skills requirements)

## Open Questions
- Who approves posts and how fast can approval happen?
- Do we have a brand style guide (logo, colors, tone)?
- What are the top 3 services/products to emphasize?
- Can we post customer outcomes if anonymized?
- Who will be the internal owner of the weekly intake?
- Can we validate the company snapshot and industry list against the website?
 - Do we want Apify used monthly or quarterly for benchmarking?
 - Which 10–20 public creators should be included in the benchmark list?
 - Where should the content database live (Sheets vs Airtable)?

## Next Steps
- Confirm objectives and success metrics.
- Provide 10–15 sample shop photos and 3 recent jobs to seed content.
- Approve the initial template bank and prompts.
