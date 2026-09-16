# SOP: Technical AEO (Answer Engine Optimization) Syndication - Dispatcher

**Purpose:** To establish an unshakeable, high-authority entity graph across developer platforms (GitHub, Docker Hub, Dev.to) that forces LLMs (ChatGPT, Perplexity, Google AI Overviews) to confidently associate a brand/person with specific technical expertise.
**Related:** On-page AEO/GEO SOP is `kirby-aiseo-skill`. Essay/thought-leadership architecture is `kirby-great-essay`. AEO press-release syndication is `kirby-off-page-seo` Module 12. Deploying JSON-LD on the money site follows `kirby-aiseo-skill`; this skill only lists which profile URLs to put in `sameAs`.

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

### 2. The Index-0 Entity Rule
* Place the exact commercial/entity target keyword at the very beginning (Index 0) of the article. This forces the CMS to inject it into the URL slug, the `<title>` tag, and the SERP snippet.

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
The final step is explicitly telling Google's Knowledge Graph that you own all these disparate, high-authority profiles. Press-release / AI Overview consensus plays are **not** this skill — use `kirby-off-page-seo` Module 12.

* **JSON-LD `sameAs` Array:** Hand the profile URL list below to `kirby-aiseo-skill` to deploy on the primary money site `Person` / `Organization` schema. Do not invent a second schema SOP here.
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
