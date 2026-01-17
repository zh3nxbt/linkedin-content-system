https://x.com/GanimCorey/status/2011883074963808258

I gave this post to Claude and asked it to build me a step by step implementation plan.

2 hours later, I have a turn key LinkedIn content machine.

Here's the entire process:

Step 1) Compile a Google sheet of the top 10 LinkedIn creators in my niche

Step 2) Sign up for Apify and got the LinkedIn Post Search Scraper for $0.10/page.

Step 3) Set up cookies, user agent, source URLs, and rate limits in Apify.

Scraped the 10 creator profiles for 900 total posts.

Step 4) Analyze the scraped data

Uploaded the 900 posts to Claude, then had it analyze the data:

• Images crush video. 70.5% of top performers were images. Only 8% were video.

• Arrows matter. Top posts use → and ↳ at 2.5x the rate of low performers.

• CTAs aren't optional. 85% of top 10% posts end with a CTA.

• Longer wins. 1,559 characters average for top posts vs 1,268 for bottom.

• Two creators to study: Charlie Hills (38% hit rate) and Ruben Hassid (36% hit rate).

Step 5) Extract patterns

• 7 hook formulas
• 6 post templates
• 30+ proven examples

All from real creator data.

Step 6) Build 2 Claude skills

linkedin-hook-writer: generates opening lines using 7 proven formulas

linkedin-post-writer: creates full posts from 6 tested templates

I also generated these assets:

hook-swipe-file: md file of 30+ top performing hooks + fill-in-the-blank templates

post-templates: md file with structures for story, contrarian, case study, list, curation, giveaway posts

pattern-playbook: md file with the data - what works, what doesn't, benchmarks

The full system in a nutshell:

Scrape creators (Apify)
↓
Analyze patterns (Claude)
↓
Generated hooks (linkedin-hook-writer skill)
↓
Write full posts (linkedin-post-writer skill)
↓
Apply my voice (brand-voice-skill)
↓
Ship content
