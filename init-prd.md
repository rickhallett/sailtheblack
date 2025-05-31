# Black Flag: Product Requirements Document

## Product Requirements Document: Shore Road Campaign Wiki

### 1. Introduction & Purpose

This document outlines the requirements for creating a centralized, accessible, and easily updatable knowledge base (wiki) for the Shore Road Campaign. The wiki will serve as the primary repository for all strategic discussions, tactical plans, research findings, communication materials, and ongoing progress related to the campaign against unfavorable changes to Shore Road traffic management in Swanage. The chosen platform will be MkDocs, with deployment via GitHub Pages, to ensure ease of use, version control, and free hosting.

**2. Goals**

*   **Centralize Information:** Consolidate all campaign-related information, strategies, and resources into a single, easily searchable location.
*   **Facilitate Collaboration:** Allow the core campaign team (Speaker and Other Speaker, plus any future volunteers) to access, contribute to, and update campaign materials efficiently.
*   **Ensure Consistency:** Maintain a consistent understanding of campaign goals, messaging, and tactics across all team members.
*   **Preserve Institutional Knowledge:** Document the campaign's journey, decisions, and learnings for current reference and potential future use or analysis.
*   **Streamline Onboarding:** Provide a comprehensive resource for quickly bringing new volunteers or collaborators up to speed.
*   **Accessibility:** Make key public-facing information (once curated) potentially available to trusted supporters or the wider public if deemed strategically beneficial.

**3. Target Users & Roles**

*   **Primary Users (Core Team):**
    *   **Speaker (Campaign Lead/Strategist):** Will use the wiki to reference strategies, track progress, refine messaging, and ensure alignment with campaign goals. Will contribute content related to social outreach, canvassing experiences, and political insights.
    *   **Other Speaker (Technical & Strategic Support):** Will use the wiki to document technical analyses (survey bias, data), manage digital assets, contribute to strategic planning, and potentially manage the wiki's technical aspects.
*   **Secondary Users (Potential Future):**
    *   **Volunteers:** If the campaign expands, volunteers could use the wiki to understand their roles, access approved messaging, and find resources for outreach. (Access levels would need to be considered).
    *   **Trusted Supporters/Advisors:** Could be given read-only access to specific sections for transparency or to solicit feedback.

**4. Functional Requirements (Features)**

*   **4.1. Content Organization & Structure:**
    *   **FR1.1 Hierarchical Navigation:** The wiki must support a clear, hierarchical navigation structure (e.g., main sections, sub-sections) mirroring the key themes identified (Core Issue, Campaign Strategy, Council Interaction, etc.).
    *   **FR1.2 Search Functionality:** Robust built-in search capability to quickly find specific information across all pages.
    *   **FR1.3 Internal Linking:** Ability to easily create hyperlinks between related pages within the wiki.
    *   **FR1.4 Table of Contents:** Automatic generation of a table of contents for longer pages.
    *   **FR1.5 Tagging/Categorization (Optional but Desirable):** Ability to tag pages with keywords for alternative browsing and filtering.

*   **4.2. Content Creation & Editing:**
    *   **FR2.1 Markdown Support:** Content creation and editing primarily through Markdown for simplicity and ease of use by both technical and non-technical users.
    *   **FR2.2 Version Control (via GitHub):** All changes to content must be tracked, allowing for rollback to previous versions and a clear audit trail.
    *   **FR2.3 Image & Media Embedding:** Ability to easily embed images (e.g., screenshots of survey, flyer designs, infographics) and potentially other media (e.g., links to audio/video if relevant).
    *   **FR2.4 Code Block Support:** For embedding any code snippets, e.g., for social media sharing or website elements (if applicable).

*   **4.3. Deployment & Hosting:**
    *   **FR3.1 GitHub Pages Integration:** Seamless deployment of the MkDocs site to a free GitHub Pages hosting environment.
    *   **FR3.2 Custom Domain (Optional Future):** Potential to map to a custom domain if the campaign grows significantly.
    *   **FR3.3 Responsive Design:** The wiki must be easily viewable and navigable on various devices (desktop, tablet, mobile).

*   **4.4. Collaboration & Access Control (via GitHub):**
    *   **FR4.1 Private Repository:** The primary GitHub repository containing the MkDocs source will be private, accessible only to the core team initially.
    *   **FR4.2 Contributor Access:** Ability to grant write access to specific individuals (core team) for content creation and updates.
    *   **FR4.3 Read-Only Access (Potential Future):** If parts of the wiki are made public or shared with a wider group, GitHub Pages provides public read-only access by default. For more granular private sharing, alternative methods or a separate public-facing site might be needed.

*   **4.5. Aesthetics & Theming:**
    *   **FR5.1 Clean & Readable Theme:** Utilize a clean, professional, and highly readable MkDocs theme (e.g., Material for MkDocs, ReadTheDocs theme).
    *   **FR5.2 Minimal Customization:** Focus on functionality and readability over complex visual customization to save time.

**5. Non-Functional Requirements**

*   **NF1.1 Ease of Use:** The system should be relatively easy for individuals with basic computer literacy to learn and use for content editing (Markdown is key here).
*   **NF2.2 Performance:** The hosted wiki should load quickly and be responsive.
*   **NF3.3 Scalability:** While initially small, the structure should allow for the addition of new sections and pages as the campaign evolves.
*   **NF4.4 Maintainability:** The MkDocs and GitHub Pages setup should be low-maintenance from a server administration perspective. Updates to MkDocs or themes should be relatively straightforward.
*   **NF5.5 Cost-Effectiveness:** Utilize free hosting (GitHub Pages) and open-source tools (MkDocs) to minimize campaign expenses.
*   **NF6.6 Security (via GitHub):** Rely on GitHub's security measures for repository access.

**6. Content Structure (Initial Proposal - to be refined)**

The wiki will be structured based on the indexed document created from the conversation transcript. Key top-level sections will include:

*   **Home/Overview:** Campaign mission, executive summary, key contacts.
*   **Core Issue: Shore Road Traffic Management:**
    *   The Survey (Analysis, Bias, Hack)
    *   Proposed Changes (One-Way vs. Two-Way)
    *   Impact on Community (Youth, Businesses, Residents)
    *   Pedestrian Safety Arguments (Council vs. Campaign)
*   **Campaign Strategy & Tactics:**
    *   Overall Goals
    *   Target Audiences (Profiles, Key Concerns)
    *   Communication & Messaging (Slogans, Framing, Tone)
    *   Tactical Plans (Flyers, Social Media, Canvassing)
    *   Data & Evidence (Survey Analysis, Traffic Data, Petitions)
    *   Networking & Alliances
*   **Council & Authority Interaction:**
    *   Council Profiles & Perceived Stances
    *   Chronology of Interactions
    *   Key Arguments for Council Presentations
    *   Freedom of Information Requests (if any)
*   **Tools & Resources:**
    *   Digital Assets (Logos, Flyer Templates, Infographics)
    *   Links to Social Media Platforms
    *   Contact Lists (Media, Councillors, Supporters)
*   **Meeting Notes & Transcripts:**
    *   (This PRD and the original conversation analysis would reside here)
    *   Future meeting summaries.
*   **Research & Data:**
    *   Links to external reports, council documents.
    *   Campaign-generated data (canvassing results, survey "hack" uptake).
*   **Timeline & Action Items:**
    *   Key deadlines (Survey, Council Meetings)
    *   Task assignments and progress tracking.

**7. Technical Stack**

*   **Documentation Generator:** MkDocs
*   **Content Format:** Markdown
*   **Version Control & Hosting:** GitHub & GitHub Pages
*   **Theme:** Material for MkDocs (recommended for features and aesthetics) or similar.

**8. Success Metrics (How will we know this wiki is useful?)**

*   **Adoption by Core Team:** Both primary users regularly access and contribute to the wiki.
*   **Information Centralization:** Key campaign information is consistently found within the wiki rather than scattered across emails or individual notes.
*   **Ease of Finding Information:** Core team members can quickly locate specific strategies, data points, or messages.
*   **Consistency of Messaging:** Public-facing communications and volunteer briefings are consistent due to reliance on wiki content.
*   **Reduced Redundancy:** Less time spent by team members asking each other for information that is already documented.

**9. Future Considerations (Out of Scope for Initial MVP)**

*   **Public-Facing Version:** Creating a separate, curated public-facing version of the wiki or parts of it.
*   **Advanced Collaboration Tools:** Integration with task management or more sophisticated collaborative editing tools if the team grows significantly.
*   **Custom Theme Development:** More advanced branding if required.

**10. Open Questions/Risks**

*   **Time Commitment for Upkeep:** Will the core team have enough time to consistently update and maintain the wiki amidst active campaigning?
*   **Markdown Proficiency:** Ensuring all core contributors are comfortable with basic Markdown.
*   **Information Overload:** As the wiki grows, maintaining a clear structure and preventing information overload will be important.

First Steps:

- [ ] rename files to standardised naming convention (black-flag--<section-number>-<filename>.md)
- [ ] format each file to use markdown formatting conventions (headings, subheadings, lists, etc)
- [ ] move to docs folder
- [ ] add mkdocs and theme (uv as package manager)
- [ ] add material theme
- [ ] add mkdocs-material
- [ ] add mkdocs-material-extensions
- [ ] configure mkdocs.yml according to above structure
- [ ] test locally with mkdocs serve and curl requests to ensure all files are being served correctly
- [ ] add appropriate hyperlinks throughout the wiki to make for a better user experience
- [ ] add a table of contents to each file
- [ ] add mkdocs search extension
- [ ] add mkdocs git-revision-date-localized-plugin
- [] final testing
- [ ] add google analytics / tag manager as per current apis
- [ ] add sitemap
- [ ] add robots.txt
- [ ] add favicon

