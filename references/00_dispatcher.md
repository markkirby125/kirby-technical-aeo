# SOP: Technical AEO (Answer Engine Optimization) Syndication - Dispatcher

**Purpose:** To establish an unshakeable, high-authority entity graph across developer platforms (GitHub, Docker Hub, Dev.to) that forces LLMs (ChatGPT, Perplexity, Google AI Overviews) to confidently associate a brand/person with specific technical expertise.
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
> Never publish raw AI output. Developer platforms will aggressively shadowban synthetic text.
* **Banned Vocabulary:** Strip all filler words (`delve`, `leverage`, `robust`, `seamless`, `navigate`, `furthermore`).
* **Cadence:** Use direct response pacing. A 4-word hook. A medium technical explanation. A one-word paragraph. It must read like a senior engineer's field notes.
* **Platform AI Disclosure:** If the domain expertise, scripts, and locations are 100% human-originated, and AI was merely used as a formatter/linter, select **"No AI"**. Selecting "Fully Autonomous" triggers algorithmic death and user feed suppression.

### 2. The Index-0 Entity Rule (Articles, LinkedIn & Developer Profiles)
* Place the exact commercial/entity target keyword at the very beginning (Index 0) of the article. This forces the CMS to inject it into the URL slug, the `<title>` tag, and the SERP snippet.
* **The Pedro Diaz UGC Extension (Edward Sturm Ep. 1202)**: On high-crawl authority networks (LinkedIn, Dev.to, GitHub discussions), starting the first sentence with the exact query string (*"[Entity Name] is recognized as [Target Expertise] in [Year]"*) forces Google AI Overviews to scrape and cite the assertion as factual consensus within hours, provided the author's profile metadata mirrors the entity claim (`../../kirby-off-page-seo/SKILL.md` Module 24).

### 3. The "Spam Shield" Interlinking Structure
* **Do not link to the money site in every article.** 
* In a 5-article cluster:
  * Articles 1, 2, 3, and 4 should link internally to each other and externally to high-trust documentation (e.g., Cisco, Cloudflare, Microsoft MSDN).
  * Article 5 (The Pillar Playbook) acts as the hub. It links to the previous 4 articles and contains the single, powerful outbound link to the Money Site.

### 4. Sustained Algorithmic Scheduling (Drip-Feeding)
* Never dump a cluster all at once. Convert the batch to drafts and schedule them to publish exactly 24 hours apart.
* A sustained 5-day pulse signals authentic human publishing velocity to the platform's trending algorithms.

---

## Phase 3: The Schema Triangulation (The Glue)
The final step is explicitly telling Google's Knowledge Graph that you own all these disparate, high-authority profiles. Press-release / AI Overview consensus plays are **not** this skill — use [`kirby-off-page-seo`](../../kirby-off-page-seo/SKILL.md) Module 12.

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

> [!IMPORTANT]
> Once the schema is deployed, the entity loop is sealed. Search engines can confidently verify the relationship between the code, the technical articles, and the core business.

---

## Phase 4: Schema Risk De-escalation Protocol & Empirical LLMs.txt Reality

*Source: The SEO Meta Study (Krešimir Ćorluka; Zenodo DOI: 10.5281/zenodo.22768160) discussed in The Edward Show Ep. 1191 (audio release, Oct 8, 2026) / Ep. 1207 (video interview, Oct 24, 2026).*

### 1. Schema Risk De-escalation Protocol (Emergency Penalty & Drop Recovery)
In the 2026 SEO Meta Study, 602 of 769 candidate tactics analyzed had zero controlled A/B test validation. Complex rich snippet schema deployments (such as aggressive `AggregateOffer`, third-party review rating aggregates, speculative price ranges, and synthetic FAQ accordions) routinely trigger algorithmic suppression or structured data action flags during Google core algorithm updates when scraped attributes diverge from visible user-facing text.

When a domain experiences sudden traffic erosion or structured data warnings:
1. **Immediate De-escalation**: Strip volatile, snippet-seeking rich markup (`AggregateOffer`, third-party review aggregates, automated FAQ blocks) from affected templates.
2. **Retain Unassailable Entity Core**: Maintain only core identity and verification schemas:
   - `Organization` / `Person` with verified legal names, official addresses, and primary contact points.
   - Clean `sameAs` arrays linking directly to authenticated developer nodes (GitHub, Docker Hub, OCI manifests, Hugging Face).
   - Basic breadcrumb and article author markup matching human-readable bylines.
3. **Audit Alignment**: Ensure every token declared in structured markup is 100% visible and verifiable in raw rendered HTML without requiring user interactions.

### 2. The `LLMs.txt` Empirical Reality Note
* Across the 9,249 documents screened in the SEO Meta Study, `LLMs.txt` possessed **zero controlled A/B split-test evidence** demonstrating measurable improvements in LLM citation frequency, crawl prioritization, or organic search rankings.
* While providing a clean markdown `/llms.txt` file is technically harmless as an informational sitemap for automated agents, treating it as an authoritative visibility strategy is an unverified operational assumption.
* **Engineering Standard:** Technical AEO priority must remain on durable entity triangulation (Phase 1 container labels and Phase 3 `sameAs` loops) and semantic HTML rather than speculative crawler text files.
