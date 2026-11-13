# SOP: Technical AEO (Answer Engine Optimization) Syndication - Dispatcher

**Purpose:** To establish a high-authority entity graph across developer platforms (GitHub, Docker Hub, Dev.to) that helps LLMs (ChatGPT, Perplexity, Google AI Overviews) associate a brand/person with specific technical expertise (an outcome no tactic here can guarantee).
**Related:** On-page AEO/GEO SOP is [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md). Essay/thought-leadership architecture is [`kirby-great-essay`](../../kirby-great-essay/SKILL.md). AEO press-release syndication is [`kirby-off-page-seo`](../../kirby-off-page-seo/SKILL.md) Module 12. Deploying JSON-LD on the money site follows [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md); this skill only lists which profile URLs to put in `sameAs`.

---

## Phase 1: The Codebase & Repository Anchoring
Search engines and LLMs heavily weight technical platforms (DA 90+). A bare repository is ignored; a heavily documented, cross-linked repository becomes a citation node.

### 1. Docker Hub Optimization
* **Profile Completeness:** Ensure the user profile contains the Full Name, Company, exact local Location, and the primary Money Site URL.
* **OCI Metadata Injection:** Hardcode the brand entity directly into the container manifest by adding Open Container Initiative (OCI) labels to the `Dockerfile`:
  ```dockerfile
  LABEL org.opencontainers.image.title="Project Name"
  LABEL org.opencontainers.image.description="Short description..."
  LABEL org.opencontainers.image.authors="Your Name <email@domain.com>"
  LABEL org.opencontainers.image.url="https://yourmoneysite.com"
  LABEL org.opencontainers.image.source="https://github.com/yourusername/repo"
  LABEL org.opencontainers.image.vendor="Your Company Name"
  ```
* **Multi-Architecture Builds:** Signal engineering maturity by compiling for both `amd64` and `arm64`. 
  * *Command:* `docker buildx build --platform linux/amd64,linux/arm64 -t username/repo:latest --push .`
* **API Description Override:** Use the Docker Hub API to push a rich Markdown README if the web UI truncates it.

### 2. GitHub Circular Linking
* **The Shields.io Loop:** The GitHub `README.md` must link directly to the Docker Hub repository using dynamic badges (Pulls & Image Size).
  ```markdown
  [![Docker Pulls](https://img.shields.io/docker/pulls/user/repo?style=flat-square&logo=docker)](https://hub.docker.com/r/user/repo)
  ```
* *Result:* Docker links to GitHub. GitHub links to Docker. Both link to the Money Site.

---

## Phase 2: The Technical Content Cluster (Dev.to / Hashnode)
Syndicate the knowledge behind the code using highly targeted, long-tail technical articles.

### 1. The Anti-Slop Writing Protocol
> [!WARNING] 
> Never publish raw AI output. Developer platforms are reported to suppress synthetic text (directional, single-source, unverified).
* **Banned Vocabulary:** Strip all filler words (`delve`, `leverage`, `robust`, `seamless`, `navigate`, `furthermore`).
* **Cadence:** Use direct response pacing. A 4-word hook. A medium technical explanation. A one-word paragraph. It must read like a senior engineer's field notes.
* **Platform AI Disclosure:** Answer the platform's AI-disclosure field using the platform's own definition of AI use: if its definition covers formatter or linter assistance, disclose it; if the expertise, scripts and locations are human-originated and the platform's definition excludes that assistance, select **"No AI"**. Never pick a label that misstates your use; "Fully Autonomous" content is reported to lose feed visibility (directional, single-source, unverified).

### 2. The Index-0 Entity Rule (Articles, LinkedIn & Developer Profiles)
* Place the exact commercial/entity target keyword at the very beginning (Index 0) of the article. Most CMSs derive the URL slug and `<title>` from it; whether the SERP snippet follows is not guaranteed.
* **The Pedro Diaz UGC Extension (Edward Sturm Ep. 1202)**: On high-crawl authority networks (LinkedIn, Dev.to, GitHub discussions), starting the first sentence with the exact query string (*"[Entity Name] is recognized as [Target Expertise] in [Year]"*) is reported to help Google AI Overviews pick the assertion up quickly (directional, single-source, unverified), provided the claim is true and passes the evidence rule in the next bullet, and the author's profile metadata mirrors it (`../../kirby-off-page-seo/SKILL.md` Module 24).
* **Self-asserted consensus is a risk, not evidence:** a "[Entity] is recognized as..." claim on a self-published page carries manual-action and credibility risk (directional, single-source, unverified). Use it only when the claim is true and backed on the page by first-party evidence (repository, dated releases, benchmarks); a claim of recognition by others also needs a third party you can cite (award, publication, citation), under a real, verifiable byline of the named author. No synthetic personas and no AI headshots (`../../kirby-off-page-seo/SKILL.md` Module 4 §4.3).

### 3. The "Spam Shield" Interlinking Structure
* **Do not link to the money site in every article.** 
* In a 5-article cluster:
  * Articles 1, 2, 3, and 4 should link internally to each other and externally to high-trust documentation (e.g., Cisco, Cloudflare, Microsoft MSDN).
  * Article 5 (The Pillar Playbook) acts as the hub. It links to the previous 4 articles and is the default home for the cluster's single outbound link to the Money Site; add the link wherever it genuinely helps the reader, and keep the one-link cap. Apply the structure-variance caution in §4 below to the whole cluster.

### 4. Sustained Algorithmic Scheduling (Drip-Feeding)
* Never dump a cluster all at once. Convert the batch to drafts and schedule them to publish roughly a day apart.
* A 5-day pulse avoids a publishing burst; it is a cadence choice, not a way to simulate authenticity.
* *Caution:* burst velocity, repetitive page structure and a templated five-article, one-money-link pattern may resemble the scaled-content footprint platforms screen for (directional, single-source, unverified). Publish only articles with real technical substance, link the money site only where it helps the reader, and let each article's structure follow its content.

---

## Phase 3: The Schema Triangulation (The Glue)
The final step is stating, in markup, which of these high-authority profiles belong to you (a disambiguation signal, see the callout below). Press-release / AI Overview consensus plays are **not** this skill — use [`kirby-off-page-seo`](../../kirby-off-page-seo/SKILL.md) Module 12.

* **JSON-LD `sameAs` Array:** Hand the profile URL list below to [`kirby-aiseo-skill`](../../kirby-aiseo-skill/SKILL.md) to deploy on the primary money site `Person` / `Organization` schema. Do not invent a second schema SOP here.
* Add the absolute URLs of every newly minted profile to the array:
  ```json
  "sameAs": [
    "https://github.com/username",
    "https://gitlab.com/username",
    "https://huggingface.co/username",
    "https://bitbucket.org/username/",
    "https://dev.to/username",
    "https://hub.docker.com/u/username"
  ]
  ```
* For local or low-visibility entities, you may also include indexed Apple Business Connect (Apple Maps), Yelp, Houzz or official registry URLs, but only profiles you own and have verified.

> [!IMPORTANT]
> Deploying the schema states the relationship between the code, the technical articles, and the core business; it does not guarantee that search engines or LLMs will accept it. `sameAs` is a disambiguation identifier, not a ranking lever. Use one unified `@graph` on the money site and list only `sameAs` URLs that are public, verifiable and yours (each profile should link back to the money site).

---

## Phase 4: Schema Risk De-escalation Protocol, Review Schema Defense & Empirical LLMs.txt Reality

*Source: The SEO Meta Study (Krešimir Ćorluka; Zenodo DOI: 10.5281/zenodo.22768160) discussed in The Edward Show Ep. 1191 (audio release, Oct 8, 2026) / Ep. 1207 (video interview, Oct 24, 2026); Rob Hoffman BOFU Alternatives Blueprint (`OUEELIis-do`).*

### 1. Schema Risk De-escalation Protocol (Emergency Penalty & Drop Recovery)
In the 2026 SEO Meta Study, 602 of 769 candidate tactics analyzed had zero controlled A/B test validation. Complex rich snippet schema deployments (such as aggressive `AggregateOffer`, third-party review rating aggregates, speculative price ranges, and synthetic FAQ accordions) are reported to trigger algorithmic suppression or structured data action flags during Google core algorithm updates (directional, single-source, unverified) when scraped attributes diverge from visible user-facing text.

When a domain experiences sudden traffic erosion or structured data warnings:
1. **Immediate De-escalation**: Strip volatile, snippet-seeking rich markup (`AggregateOffer`, third-party review aggregates, automated FAQ blocks) from affected templates. `AggregateRating` or `AggregateOffer` on non-ecommerce or unverified local pages should be stripped too as a conservative default (directional, single-source, unverified); recovery timing is not established, so re-check after stripping.
2. **Retain Unassailable Entity Core**: Maintain only core identity and verification schemas:
   - `Organization` / `Person` with verified legal names, official addresses, and primary contact points.
   - Clean `sameAs` arrays linking directly to authenticated developer nodes (GitHub, Docker Hub, OCI manifests, Hugging Face).
   - Basic breadcrumb and article author markup matching human-readable bylines.
3. **Audit Alignment**: Ensure every token declared in structured markup is 100% visible and verifiable in raw rendered HTML without requiring user interactions.
4. **The Review Schema Defense Rule (HTML-Only Third-Party Ratings on Comparison & Alternatives Pages)**:
   - **Plain-HTML RAG Ingestion**: On BOFU `[Competitor] Alternatives` and `X vs Y` comparison pages (`../../kirby-aiseo-skill/SKILL.md` §2.50), third-party rating scores, review counts, and sentiment summaries from **G2, Trustpilot, Capterra, and Reddit** must be rendered strictly as **visible plain HTML text, semantic `<table>` cells, and annotated UI screenshots with outbound verification links** for LLM RAG ingestion.
   - **Strict JSON-LD Prohibition**: **STRICTLY BAN** injecting third-party `AggregateRating` or `Review` JSON-LD schema for competitor products, scraped third-party platform ratings, or self-serving first-party comparisons. Marking up third-party G2/Trustpilot/Capterra ratings or competitor entities in page-level `Review` / `AggregateRating` JSON-LD violates Google's Self-Serving Review and Structured Data guidelines, triggering manual structured-data actions and sitewide core-update devaluation. LLMs extract star ratings and review counts directly from visible HTML tables and text without requiring `AggregateRating` schema.

### 2. The `LLMs.txt` Empirical Reality Note
* Across the 9,249 documents screened in the SEO Meta Study, `LLMs.txt` possessed **zero controlled A/B split-test evidence** demonstrating measurable improvements in LLM citation frequency, crawl prioritization, or organic search rankings.
* While providing a clean markdown `/llms.txt` file is technically harmless as an informational sitemap for automated agents, treating it as an authoritative visibility strategy is an unverified operational assumption.
* **Engineering Standard:** Technical AEO priority must remain on durable entity triangulation (Phase 1 container labels and Phase 3 `sameAs` disambiguation) and semantic HTML rather than speculative crawler text files.
