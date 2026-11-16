# **1. Product Requirement Document (PRD)** 

|**Feature /**<br>**Module**|**Specification & Business Logic**|
|---|---|
|**Brand**<br>**Positionin**<br>**g**|**Hyperknot Digital PR & Branding**(Kochi, Kerala). Full-service digital<br>marketing, brand architecture, and digital PR consultancy bridging the<br>gap between current standing and undeniable market authority.|
|**Key Trust**<br>**Anchor**|**10+ Years of Social Media & Brand Mastery**highlighted prominently via<br>an interactive 3D milestone badge and animated metrics counter across<br>the Home and Services views.|
|**Multi-Page**<br>**Architectu**<br>**re**|1.**Home (/)**: Scroll-driven 3D WebGL experience, "K N [O] T" portal hero,<br>The Hyperknot Edge, 4 Core Services stack, Featured Accordion.<br>2.**The Lab / Strategy (/strategy)**: Educational & high-converting authority<br>page breaking down the_Science & Psychology of Marketing_.<br>3.**Pricing & Packages (/pricing)**: Transparent 3-Tier Digital Marketing<br>retainers (₹25k, ₹45k, ₹85k+) + Custom Consultation triggers for Film PR,<br>Inauguration PR, & B2B Consulting.|
||4.**Contact & Booking (/contact)**: Direct functional triggers for WhatsApp<br>(walink.me/5zhy59), Email (hyperknotpr@gmail.com), Instagram<br>(@hyperknotpr), and webhook form.|
|**Functional**<br>**Action**<br>**Links**|•**WhatsApp:**[https://walink.me/5zhy59](https://walink.me/5zhy59)<br>(Opens native WhatsApp app/web in new tab with rel="noopener<br>noreferrer").<br>•**Email:**mailto:hyperknotpr@gmail.com?subject=Project%20Inquiry%20-|



|**Feature /**<br>**Module**|**Specification & Business Logic**|
|---|---|
||%20Hyperknot|
||•**Instagram:**<br>[https://www.instagram.com/hyperknotpr/](https://www.instagram.com<br>/hyperknotpr/)|
|**Target**<br>**Audience**|Multi-branch regional businesses, real estate builders, Malayalam cinema<br>production houses, corporate founders, and B2B enterprises across<br>Kerala.|
|**2. Technical R**|**equirement Document (TRD)**|



|**Layer**|**Technical Stack & Skill Alignment**|
|---|---|
|**Core**<br>**Framework**|**Next.js 14+ (App Router)**with TypeScript & React Server<br>Components (vercel-react-best-practices).|
||**Three.js + React Three Fiber (@react-three/fiber) +**<br>**@react-three/drei**(threejs-fundamentals, threejs-materials, threejs-<br>lighting, threejs-interaction).|
|**3D & WebGL**<br>**Engine**|• Custom 3D Torus Knot / Hyper-Knot centerpiece in the Hero and<br>Strategy pages using physical transmission materials<br>(MeshTransmissionMaterial) tinted with #4382DF and #4647AE.|
||• Mouse-reactive parallax camera rig and instanced particle field<br>(threejs-performance).|
|**Scroll & UI**<br>**Motion**|**Framer Motion**(useScroll, useTransform, AnimatePresence) +**Lenis**<br>**Smooth Scroll**synced to the Three.js useFrame render loop.|



|**Layer**|**Technical Stack & Skill Alignment**|
|---|---|
||Governed by addyosmani/web-quality-skills & threejs-performance:|
||• Dynamic dpr={[1, 1.5]} clamping on mobile GPUs.|
|**Performance &**<br>**Quality**|• Draco compression for any .glb models (threejs-loaders, threejs-<br>asset-pipeline).|
||• Automatic fallback to lightweight CSS/Shader gradients on low-<br>power mobile devices (prefers-reduced-motion).|
||• Core Web Vitals targets: LCP less than 2.5s, CLS less than 0.05, INP<br>less than 200ms.|
|**Deployment**|**Vercel**(deploy-to-vercel), configured with Edge caching and<br>automatic image optimization (next/image).|



# **3. Design Brief Document** 

- **3.1 Color Architecture (Cyber-Executive Deep Blue Palette)** 

   - **Primary Deep Canvas (#112E81 - Deep Navy):** Global dark background anchor, footer surface, and deep 3D fog color. 

   - **Secondary Surface (#4647AE - Brand Indigo):** Stacking service cards, glassmorphic pricing card borders, and ambient 3D point lights. 

   - **Interactive & Accent (#4382DF - Bright Electric Blue):** Primary CTA buttons, the scaling Hero [O] portal, active pricing tier highlights ("The Growth Package"), and 3D emissive wireframes. 

   - **Highlight & Micro-Typography (#AACCD6 - Ice Blue):** Uppercase tracking labels, technical badges ("10+ YEARS EXPERIENCE"), subtle grid lines, and secondary body copy. 

- **Contrast Base (#060913 & #FFFFFF):** Ultra-dark void background for WebGL canvas contrast; crisp #FFFFFF for H1/H2 display typography. 

# **3.2 Logo & Visual Assets** 

- **Logo Placement:** /public/logo.png (or /public/logo.svg) placed in the floating glassmorphic pill Navbar (top-4, z-50) alongside the bold HYPERKNOT wordmark. 

- **3D Visual Trickery ("Mind-Blowing Client Experience"):** 

   - **Hero Section:** While scrolling through the 400vh container, inside the scaling #4382DF circle (K N [O] T), render a live interactive **3D Metallic/Glass HyperKnot** that twists and refracts the background video based on scroll velocity and cursor position. 

   - **Cursor Magnetic Field:** On desktop, buttons and pricing cards subtly pull toward the cursor with a glowing #4382DF radial spotlight following the mouse. 

# **4. Backend Schema & Content Data Document** 

Since the site operates at blazing speed without heavy database overhead, static structured data is stored in /src/data/hyperknotData.ts and dynamic inquiries route via serverless API / Webhooks. 

TypeScript // /src/types/schema.ts 

export interface ServicePillar { id: string; number: string; title: string; accentColor: string; // #112E81 | #4647AE | #4382DF videoUrl: string; subServices: { name: string; description: string; }[]; } 

export interface PricingTier { 

id: string; name: string; price: string; billingCycle: string; bestFor: string; isPopular?: boolean; features: { category: string; detail: string; }[]; ctaText: string; whatsappPrefill: string; // Appended to https://walink.me/5zhy59 or custom wa.me link } 

export interface BespokeVertical { 

id: string; 

title: 'Film & Entertainment PR' | 'Business Inauguration PR' | 'B2B Strategic Consulting' | 'Custom Brand Architecture'; 

badge: 'Consultation Required'; description: string; deliverables: string[]; 

bookingAction: string; // Triggers direct meeting modal or WhatsApp 

} 

export interface LeadSubmissionPayload { 

timestamp: string; 

clientName: string; 

companyOrProject: string; 

phoneOrWhatsapp: string; 

email: string; 

inquiryType: 'Tier 1 (₹25k)' | 'Tier 2 (₹45k)' | 'Tier 3 (₹85k+)' | 'Film/Inauguration PR' | 'B2B Consulting'; 

message: string; 

} 

# **5. App Flow & Page-by-Page Content Blueprint** 

**Page 1: Home (/) —** **_The Authority Engine_** 

1. **Floating Pill Navbar:** Logo (/logo.png + HYPERKNOT), Links (Home, Services, The Strategy Lab, Pricing, Contact), plus an instant "WhatsApp Us" neon pill button ([https://walink.me/5zhy59](https://walink.me/5zhy59)). 

2. **Hero (400vh Scroll-Scrubbed + 3D WebGL):** 

   - Opens with giant K N [O] T typography. The [O] houses the #4382DF circle + live 3D Glass Torus Knot. 

   - Scroll 0.15 - 0.45: Reveals _"10+ Years of Engineering Market Authority."_ 

   - Scroll 0.45 - 0.85: Reveals _"Bridging the Gap Between Where You Are and the Market Authority You Deserve."_ with dual CTAs (Explore Packages & Book Strategy Call). 

3. **The 10-Year Mastery & "Hyperknot Edge" Bento Grid:** 

   - 4 Interactive 3D Tilt Cards: **The Authority-First Model** , **Turnkey Production to Distribution** , **Hyper-Localized Market Acumen (Kerala & Beyond)** , and **DataBacked Commercial Impact** . 

4. **Core Services (300vh 3D Stacking Cards):** 

   - **Card 01 (#112E81):** Brand Identity & Visual Architecture (Brand Strategy, Corporate Identity, Digital Storefront Makeovers). 

   - **Card 02 (#4647AE):** Digital PR & Authority Building (Executive/Founder Branding, Reputation & Media Positioning, Social Proof Systems). 

   - **Card 03 (#4382DF):** Full-Stack Content Production & Social Strategy (10-Year Expertise highlight, End-to-End Reels/Shorts Production, Multi-Platform Management, Visual Feeds). 

   - **Card 04 (#0d1f5c):** Performance Marketing & Automated Lead Gen (Meta/Google Funnels, Local SEO, WhatsApp/Telegram Webhook Inquiry Funnels). 

5. **Interactive Accordion Showcase:** Hover-expanding showcase for Film PR campaigns, Corporate Branding, Inauguration Launches, and B2B Growth. 

**Page 2: The Strategy Lab (/strategy) —** **_Why Real Marketing Isn't Mechanical_** 

**Page Purpose:** Educate and impress high-ticket clients before they even look at pricing. Prove that posting random graphics or boosting posts without architecture is burning money. 

- **Interactive 3D Header:** A 3D neural-network/knot simulation with four glowing nodes: **Emotion** , **Cognitive Psychology** , **Statistical Data** , and **Technical Automation** . Clicking or scrolling through each node transforms the 3D geometry and reveals the strategy breakdown: 

- **Section 1: The Death of "Mechanical" Marketing** 

   - _The Trap:_ Most businesses treat marketing like a factory checklist—post 3 graphics a week, boost a post for ₹500, and hope for miracles. 

   - _The Reality:_ Attention in 2026 is won in **1.7 seconds** . Without psychological hooks and algorithmic engineering, volume equals zero commercial impact. 

- **Section 2: The 4 Pillars of High-Converting Marketing (Interactive Deep-Dive)** 

   1. **Cognitive Psychology & Behavioural Economics (The Brain):** 

      - _The Halo Effect & Authority Bias:_ Why a founder or brand positioned as an industry expert commands 40% higher pricing with lower sales resistance. 

      - _Loss Aversion & Anchoring:_ Structuring offers so prospects feel the cost of _inaction_ rather than the cost of your service. 

      - _The Mere-Exposure Effect:_ Engineering omnichannel frequency (Instagram Reels + YouTube Shorts + Google Search + LinkedIn) so your brand feels like the only safe choice in Kerala. 

   2. **Emotional Resonance & Cinematic Storytelling (The Heart):** 

      - _Dopamine & Pattern Interrupts:_ How we script the first 3 seconds of a Reel—using visual velocity, sound design, and curiosity gaps to stop the thumb scroll. 

      - _Identity-Driven Buying:_ People don't buy construction, clinics, or retail products; they buy status, security, and aspiration. 

# 3. **Statistical Rigor & Funnel Math (The Numbers):** 

   - _Vanity Metrics vs. Revenue Metrics:_ Why 100,000 irrelevant views mean nothing compared to 50 high-intent local leads at a predictable Cost-Per-Acquisition (CPA). 

   - _A/B Multivariate Testing:_ Testing hook retention rates (3-second view vs. 50% watch time) and landing page conversion rates mathematically. 

4. **Technical Architecture & Speed-to-Lead (The Machine):** 

   - _The 5-Minute Lead Decay Rule:_ Statistics show that waiting more than 5 minutes to contact an inbound digital lead drops conversion probability by **80%** . 

   - _The Hyperknot Webhook Engine:_ How we connect Meta/Google Lead Forms directly into instant Telegram/WhatsApp alerts so your sales team strikes while the buyer's intent is at peak temperature. 

**Page 3: Pricing & Investment (/pricing) —** **_Transparent Retainers + Bespoke PR_** 

# **Part A: Monthly Digital Marketing & Growth Packages (3-Column Interactive Glass Cards)** 

- **Tier 1: THE BASIC PACKAGE — ₹25,000 / MONTH** 

   - _Tagline:_ Best for local shops or single-branch businesses needing a professional presence and steady leads. 

   - _Deliverables List:_ 6 Reels/Shorts + 4 Graphics + Festival Posts | IG, FB, YT (with thumbnails) | Google Business (1 post/wk + reviews) | Free LinkedIn CrossPosting | Meta/Google Lead Ads Management (ad spend extra) | Google Maps & WhatsApp Business Setup | General Tech & Design Support. 

   - _CTA:_ Clickable button → [https://walink.me/5zhy59](https://walink.me/5zhy59) 

#  **Tier 2: THE GROWTH PACKAGE — ₹45,000 / MONTH (Highlighted with #4382DF Glow & "MOST POPULAR" Badge)** 

- _Tagline:_ Best for real estate projects, clinics, and mid-sized retail requiring aggressive lead volume and faster response times. 

- _Deliverables List:_ 10 Reels/Shorts + 8 High-Fidelity Graphics + Festival Posts | IG, FB, YT + Active LinkedIn Management | Google Business & Local SEO (2 posts/wk, Q&A seeding, local keyword ranking) | Multi-campaign Meta & Google Ads (Search + PMax) with weekly A/B testing | **Pipeline Automation** (Instant Facebook/Google lead routing to WhatsApp/Telegram via webhooks) 

| **1 Custom Landing Page** design & hosting | Bi-weekly review & priority design support. 

   - _CTA:_ Clickable button → [https://walink.me/5zhy59](https://walink.me/5zhy59) 

- **Tier 3: THE DOMINANCE PACKAGE — ₹85,000+ / MONTH** 

   - _Tagline:_ Best for multi-branch brands, top-tier builders, and businesses wanting to dominate their category across Kerala. 

   - _Deliverables List:_ 15 Reels/Shorts (scriptwriting + storyboarding) + 15 Graphics + Campaign Posters | Full Omnichannel Management + Community Engagement (DM/Comment replies per brand guideline) | Complete On-Page & Off-Page Website SEO + Localized Backlinks | Full-Funnel Ad Strategy (Awareness + Retargeting + Lead Gen on Meta, Google, YT) | **Ecosystem Automation** (CRM integration, automated Email/WhatsApp cold-lead followups, transaction logging) | **Live Custom Analytics Dashboard** (real-time CPL & ROI) | Dedicated WhatsApp Group + Monthly Strategy Consultation. 

   - _CTA:_ Clickable button → [https://walink.me/5zhy59](https://walink.me/5zhy59) 

# **Part B: Custom & Bespoke Engagements (Direct Consultation Required)** 

Displayed right below the packages as an executive dark-glass vault section: _"Because every film release, grand inauguration, and B2B ecosystem has unique territorial and media requirements, the following verticals are custom-scoped after a direct in-person or online strategy briefing."_ 

1. **Malayalam Cinema & Entertainment PR:** Pre-release buzz, trailer/poster launch amplification, influencer & media orchestration, theatre-level digital dominance. _(Price: Decided Post-Discussion)_ 

2. **Grand Business Inauguration & Launch PR:** Pre-launch teaser campaigns, media coverage, VIP/influencer coordination, on-ground live reel production, and hyperlocal footfall ads. _(Price: Decided Post-Discussion)_ 

3. **B2B Marketing & Strategic Middleman Consulting:** Connecting enterprise partners, structuring B2B deal pipelines, executive LinkedIn ghostwriting, and corporate pitch architecture. _(Price: Decided Post-Discussion)_ 

4. **Standalone Brand Identity & Custom Web/3D Architecture:** Complete rebrands, packaging, and custom interactive websites. _(Price: Decided Post-Discussion)_ 

# **Page 4: Contact & Direct Channels (/contact + Global Knockout Footer)** 

- **Direct Action Hub (100% Functional Clickable Cards):** 

- **Instant WhatsApp Chat:** 

[https://walink.me/5zhy59](https://walink.me/5zhy59) (Opens immediately in new tab with pulsing green/blue status indicator). 

   - **Direct Email Dispatch:** mailto:hyperknotpr@gmail.com (Displays hyperknotpr@gmail.com with both a direct mailto: trigger and a 1-click "Copy Email" toast button). 

   - **Instagram Portfolio & Reels:** [https://www.instagram.com/hyperknotpr/] (https://www.instagram.com/hyperknotpr/) (Opens @hyperknotpr with live preview aesthetic). 

- **Interactive Discovery Form:** Allows prospects to select either a fixed package (₹25k, ₹45k, ₹85k+) or request a **Custom Briefing (PR / B2B / Inauguration)** , routing straight to WhatsApp or your webhook. 

- **Global Knockout Video Footer:** Giant LET'S TALK. text (mix-blend-multiply) hovering into #4382DF. 

# **6. Implementation Plan Document** 

|**Phase**|**Milestone & Skill Execution**|
|---|---|
|**Phase 1:**<br>**Project**<br>**Scaffolding**<br>**& Design**<br>**Tokens**|Initialize Next.js App Router, Tailwind CSS (#112E81, #4647AE, #4382DF,<br>#AACCD6), Three.js (@react-three/fiber, @react-three/drei), Framer<br>Motion, and Lucide Icons. Place logo in /public/logo.png.|
|**Phase 2:**<br>**3D WebGL**<br>**Scene &**<br>**Scroll Hero**|Build the <HyperknotCanvas/> using threejs-fundamentals, threejs-<br>materials, and threejs-performance. Integrate the 400vh K N [O] T scroll-<br>scrubbing portal and 10-year expertise badge.|
|**Phase 3:**||
|**Core**<br>**Services**<br>**Stack &**<br>**Strategy**|Build the -mt-[100vh] 3D stacking cards for the 4 core services and the<br>/strategy interactive psychology & funnel math experience (frontend-<br>design).|
|**Lab**||
|**Phase 4:**|Build /pricing with the 3 detailed tiers + the Bespoke PR/B2B consultation|



|**Phase**|**Milestone & Skill Execution**|
|---|---|
|**Pricing**<br>**Engine &**<br>**Live**<br>**Contact**<br>**Routing**|vault. Wire [https://walink.me/5zhy59](https://walink.me/5zhy59),<br>mailto:hyperknotpr@gmail.com, and<br>[https://www.instagram.com/hyperknotpr/](https://www.instagram.com<br>/hyperknotpr/) across all CTAs.|
|**Phase 5:**<br>**Web**||
|**Quality**|Run addyosmani/web-quality-skills and vercel-react-best-practices audits|
|**Audit &**|(accessibility, mobile touch responsiveness, WebGL frame-rate capping,|
|**Vercel**|SEO metadata) and deploy via deploy-to-vercel.|
|**Deployme**<br>**nt**||



