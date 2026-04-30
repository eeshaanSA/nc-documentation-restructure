# Nextcloud documentation restructure - Approach 2

Prepared by Eeshaan Sawant for the Nextcloud Developer Relations challenge.

## Summary - Approach 2

[The Nextcloud Developer Manual](https://docs.nextcloud.com/server/latest/developer_manual/) has grown organically over time, as engineers added and updated content. While the content is technically strong, some structural issues make it harder to find things, especially the API documentation. Navigation to and through some other sections can also be difficult for many audiences, including newer developers and designers.

Approach 2 takes a different path from Approach 1. Instead of major reconstruction of the developer manual, it focuses on solving the impactful problems with minimal changes to the current structure/hierarchy.

This approach:

- Isolates scattered pages and sub-sections related to APIs into a new section called "API Reference". This helps (and, in the future, will help) keep everything related to APIs in a single section. The "API Reference" is a top-level section, and also introduces a new page called 'API Overview'.
- Renames Digging Deeper to "Extending Nextcloud", and the top-level section previously called "Basic Concepts" is now just "Concepts". Most pages and sub-sections remain the same. Content related to APIs is moved to "API Reference".
- Isolates design and front-end styling, and bundles it under a single "Design Guidelines" section.

## Current Structure

For a detailed walkthrough of the current developer manual, including the flowchart, sidebar screenshots, and full hierarchy mapping — please refer to the [Approach-1 README](../Approach-1/README.md#current-structure). This document builds on the same analysis but proposes a different set of changes that solve a different problem than Approach 1.

### Major issues to solve with the current structure

#### 1. Digging Deeper section

The "Digging Deeper" section contains over 40 pages covering a large array of topics. Among them are several that deserve much better discoverability, such as the REST API and JavaScript API references.

The latest version (compared to older versions) does group these pages into meaningful categories, including a dedicated one for APIs. However, those API pages remain isolated from other API types like OCP and OCS, which live in entirely different sections.

#### 2. API Documentation is scattered across multiple sections (common goal with Approach-1)

Here's how the major API references are structured in the current manual:

| API | Current location |
| --- | --- |
| **OCP** (PHP Public API) | Digging Deeper → APIs & Integration → API reference |
| **OCS** (REST API) | Clients and Client APIs → OCS API |
| **WebDAV** | Clients and Client APIs → WebDAV |
| **REST API development** | Digging Deeper → APIs & Integration → REST APIs |
| **JavaScript APIs** | Digging Deeper → APIs & Integration → JavaScript APIs |
| **External API** | Server Development → External API |

This layout causes many issues — for example, a developer needing OCP API + REST API finds them in two different top-level sections, and an external integration needing OCS + WebDAV may not look in "Clients and Client APIs" because the name implies it is for clients. The most prominent issue, however, is the lack of a unified API landing page. That is why, in the proposed structure, I have introduced a dedicated landing page that explains what each Nextcloud API is and what it can do, and then directs developers organically to the required documentation.

I have also amalgamated most API references into the new "API Reference" section (which you can see below), without losing the context, which is one of the main goals of this restructuring approach.

#### 3. Duplicated content across sections

Some topics are covered by more than one page in different sections. Rather than restructuring around this, I merged the overlapping pages and placed each in the section where it fits best.

## Proposed top-level structure

```mermaid
graph LR
    root["Nextcloud Developer Manual<br/><i>Approach-2</i>"]

    root --> S1["1. Prologue"]
    root --> S2["2. Getting Started"]
    root --> S3["3. Concepts"]
    root --> S4["4. API Reference"]
    root --> S5["5. App Development"]
    root --> S6["6. ExApp Development"]
    root --> S7["7. App Publishing &<br/>Maintenance"]
    root --> S8["8. Server Development"]
    root --> S9["9. Extending Nextcloud"]
    root --> S10["10. Design Guidelines"]
    root --> S11["11. Client Development"]
    root --> S12["12. Release Notes"]
```

## In-depth hierarchy of each section

```md
 1. Prologue
    ├── Code of conduct
    ├── Help & communication
    ├── Reporting bugs
    └── Compatibility with app ecosystem

 2. Getting Started
    ├── Development process
    ├── Development environment
    └── Coding style & guidelines

 3. Concepts
    ├── Request lifecycle
    ├── Routing
    ├── Nextcloud architecture
    ├── Filesystem API
    ├── Dependency injection
    ├── Controllers
    ├── Middlewares
    ├── Events
    ├── Front-end
    ├── Translations
    ├── Background jobs (Cron)
    ├── Caching
    ├── Logging
    ├── Settings
    ├── Storage and database
    ├── Public share template
    └── Testing PHP code

 4. API Reference
    ├── API Overview
    ├── OCP: PHP Public API
    ├── OCS: REST API
    │   ├── OCS overview & conventions
    │   ├── OpenAPI specification tutorial
    │   ├── Share API
    │   ├── Sharee API
    │   ├── Status API
    │   ├── User Preferences API
    │   ├── Out-of-office API
    │   ├── TaskProcessing API
    │   ├── Translation API
    │   ├── TextProcessing API
    │   ├── Text-To-Image API
    │   ├── FullTextSearch Collections API
    │   └── Recommendations API
    ├── WebDAV API
    │   ├── Basic operations
    │   ├── File search (REPORT)
    │   ├── Trashbin
    │   ├── File versions
    │   ├── Chunked upload
    │   ├── Bulk upload
    │   └── Comments
    ├── REST API Development
    ├── JavaScript APIs
    └── External API

 5. App Development
    ├── Introduction
    ├── Tutorial
    ├── Bootstrapping
    ├── App metadata
    ├── Navigation & pre-app configuration
    ├── Dependency management
    ├── Extending the DAV server
    ├── Translation
    └── Security guidelines

 6. ExApp Development
    ├── Introduction
    ├── Setting up dev environment
    ├── Development overview
    ├── Technical details
    └── FAQ

 7. App Publishing & Maintenance
    ├── Maintainers
    ├── Release process
    ├── Publishing App on the App Store
    ├── Monetizing your app
    ├── App Store rules
    ├── Code signing
    ├── Release automation
    └── App upgrade guide

 8. Server Development
    ├── Front-end code
    ├── Back-end code
    ├── Static analysis
    └── Testing Integrations
        ├── Email sending
        ├── Redis / Redis Cluster
        ├── S3 object storage
        ├── SMB external storage
        ├── SAML with OneLogin
        ├── Collabora without SSL
        ├── OnlyOffice
        └── WebAuthn without SSL

 9. Extending Nextcloud
    ├── AI & Machine Learning
    │   ├── Task Processing
    │   ├── Context Chat
    │   ├── Machine Translation
    │   ├── Speech-To-Text
    │   ├── Text Processing
    │   └── Text-To-Image
    ├── Users & Authentication
    │   ├── User management
    │   ├── User migration
    │   ├── Profile
    │   ├── User Status
    │   ├── Out-of-office periods
    │   ├── OpenID Connect (OIDC)
    │   └── Two-factor providers
    ├── Groupware & Workflows
    │   ├── Groupware integration
    │   ├── Nextcloud Flow
    │   └── Projects
    ├── Search & Discovery
    │   ├── Search
    │   ├── Reference providers
    │   └── Files Metadata
    ├── Development Tools
    │   ├── Debugging
    │   ├── Profiler
    │   ├── Continuous Integration
    │   ├── NPM
    │   ├── Performance considerations
    │   ├── Classloader
    │   └── PSR
    └── Server Internals
        ├── Config & Preferences
        ├── Settings
        ├── Security
        ├── Deadlocks
        ├── Snowflake IDs
        ├── Working with time
        ├── Open Metrics exporter
        ├── Phone number util
        ├── Setup checks
        ├── Repair steps
        ├── WebDAV collection preload events
        ├── Dashboard
        ├── Email
        ├── HTTP Client
        ├── Notifications
        ├── Public Pages
        ├── Talk Integration
        └── Web Host Metadata

10. Design Guidelines
    ├── Introduction
    ├── Foundations
    ├── Layout
    ├── Layout components
    ├── Atomic components
    ├── Navigation
    ├── Main content
    ├── Content list
    ├── Popover menu
    ├── HTML elements
    ├── CSS
    └── Icons

11. Client Development
    ├── General
    ├── Activity
    ├── Android library
    ├── Files
    ├── Login Flow
    ├── Remote wipe
    ├── Client Integration
    └── Building the desktop client

12. Release Notes
    ├── Critical changes
    ├── New in this release
    ├── Deprecations
    └── Previous release notes
```

### Summary of changes from the current structure

This approach is a lighter-touch restructuring than Approach 1 — it keeps the overall shape of the existing manual but applies targeted renames, merges, and moves to address the most painful navigation issues.

#### Renames without changes

- *Bugtracker* → **Reporting bugs**
- *Basic Concepts* → **Concepts** (dropped "Basic"; the section covers core architecture, not just basics).
- *Digging Deeper* → **Extending Nextcloud**
- *Clients and Client APIs* → **Client Development**
- *Interface & Interaction Design* + *HTML/CSS Guidelines* → **Design Guidelines** (single merged section).
- *Server Development/How to test...* → **Testing Integrations**.

Here is a Proof of Concept (POC) for how the sidebar will look:

![Proposed Sidebar](./src/img/sidebar-proposed.png)

#### New section (API Reference)

- **API Reference** — a new top-level section that consolidates all API documentation (OCP, OCS, WebDAV, REST API Development, JavaScript APIs, External API) in one place. Includes a new **API Overview** landing page, [similar to Approach-1](../Approach-1/README.md#4-api-reference).

Here is a flowchart to understand the API Reference structure better:

```mermaid
graph LR
    S4["4. API Reference"] --> Overview["API Overview"]
    S4 --> OCP["OCP: PHP Public API"]
    S4 --> OCS["OCS: REST API"]
    S4 --> WebDAV["WebDAV API"]
    S4 --> REST["REST API Development"]
    S4 --> JS["JavaScript APIs"]
    S4 --> Ext["External API"]

    OCS --> OCS1["OCS overview & conventions"]
    OCS --> OCS2["OpenAPI tutorial"]
    OCS --> OCS3["Share API"]
    OCS --> OCS4["Sharee API"]
    OCS --> OCS5["Status API"]
    OCS --> OCS6["User Preferences API"]
    OCS --> OCS7["Out-of-office API"]
    OCS --> OCS8["TaskProcessing API"]
    OCS --> OCS9["Translation API"]
    OCS --> OCS10["TextProcessing API"]
    OCS --> OCS11["Text-To-Image API"]
    OCS --> OCS12["FullTextSearch Collections"]
    OCS --> OCS13["Recommendations API"]

    WebDAV --> W1["Basic operations"]
    WebDAV --> W2["File search"]
    WebDAV --> W3["Trashbin"]
    WebDAV --> W4["File versions"]
    WebDAV --> W5["Chunked upload"]
    WebDAV --> W6["Bulk upload"]
    WebDAV --> W7["Comments"]
```

Here is a POC of how the new landing page will look:

![API Reference landing page](./src/img/api-landing-page.png)

#### Moves

- *Nextcloud architecture* and *Filesystem API* → moved from Server Development into **Concepts**.
- *Security guidelines* → moved from Prologue into **App Development**; primarily addresses app authors.
- *Building the desktop client* → moved from the *Desktop Clients* section into **Client Development**.
- All API pages (OCP, OCS, WebDAV, REST API Development, JavaScript APIs, External API) → moved to the new **API Reference** section.

Although this restructuring might look the same as before, and has roughly the same number of top-level sections (12), the API discoverability has been greatly improved, important concepts have been grouped together (either placed in the same section or merged from two pages into one), and several confusing names and texts have been made clearer.

>**Note:**
>All the Proof of Concept (POC) screenshots have been made using my personal fork of the Nextcloud/documentation repository. The changes are made with the help of GitHub Codespaces and GitHub Copilot. Please take a look at [the fork](https://github.com/eeshaanSA/nc-documentation/) for more details.

## Caveats

Although this approach promises a minimal restructure and a simpler development curve, there are several limitations that follow:

- **Contributor welcoming and onboarding problem remains unsolved.** There is no clear layout for people looking for steps to contribute to the Nextcloud code. While it is generally assumed that such details are usually found in either the GitHub repo's README.md or CONTRIBUTING.md, having a dedicated section in the developer manual, or at least isolating current pages that talk about contributing (which are currently dispersed across "Prologue", "Getting Started", etc), into one section will help streamline the journey of developer looking for more details to contribute to Nextcloud code.
- **Concepts of "App development" are also dispersed across multiple sub-sections** in "Getting Started" and these can potentially be put under one section, so everything related to App development can be found under a single section.

Overall, this restructuring is easier, promises a good developer experience, and can be delivered within a couple of weeks. The trade-offs above are relatively minor, but depending on what a given reader is looking for, they can significantly affect the documentation experience — and are worth acknowledging and fixing over time.

## Relationship to Approach 1

While Approach 1 can be considered the end goal and an ideal long-term structure for the developer manual, Approach 2 can be the first step in achieving the hierarchy in Approach-1. It tackles three important problems to start with — API discoverability, the bloated "Digging Deeper" section, and the scattered design/front-end guidelines — while reorganizing only a minimal set of files (fewer than 15) overall to drastically improve the developer experience.

Approach-2, if adopted as the first step in improving the overall structure of the developer manual, will ensure minimal rework and will preserve any work done toward future migrations. Any subsequent migration toward Approach-1 (or another target structure) will build on this foundation rather than discarding it completely or redoing it from scratch.

## References

- **Diátaxis Framework** — [diataxis.fr](https://diataxis.fr) — The separation of API Reference as a dedicated section follows the Diátaxis principle of keeping reference material (lookup) separate from tutorials and how-to guides.

- **Stripe Documentation** — [docs.stripe.com](https://docs.stripe.com) — The API Overview landing page is inspired by Stripe's approach of routing developers by intent.
