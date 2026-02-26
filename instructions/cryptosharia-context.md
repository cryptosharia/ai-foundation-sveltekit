# CryptoSharia Context

This document gives AI shared business and ecosystem context for CryptoSharia (PT Kripto Syariah Indonesia) SvelteKit applications.

## Company Snapshot

- **Legal Name**: PT Kripto Syariah Indonesia
- **Mission**: Build Sharia-compliant crypto education and products for Indonesian Muslims.
- **Core Promise**: Help users navigate crypto "the halal way" through trustworthy media, education, and community.
- **Operating Style**: Trust-first, education-first, long-term value over hype.

## Problem Space

Crypto users are often exposed to noisy, speculative, and conflicting information. CryptoSharia exists to provide:

- Practical guidance grounded in Islamic values.
- Structured content that reduces confusion for beginners.
- Trusted products across identity, content, learning, and community.

## Target Audience and Personas

- **Muslim crypto beginners**: need clear, safe, jargon-light explanations.
- **Learning-focused members**: need deeper research, token screening, and educational progression.
- **Internal operators/admins**: need reliable tools to manage users, content, and platform quality.

## Ecosystem Platforms

- **CryptoSharia Profile** - company profile and public landing
- **CryptoSharia Accounts** - centralized authentication and SSO
- **CryptoSharia Admin** - internal CMS and operations dashboard
- **CryptoSharia Media** - content hub, news, research, token screenings
- **CryptoSharia Community** - member portal and community landing
- **CryptoSharia Academy** - learning management system
- **CryptoSharia Store** - payments, subscriptions, products
- **CryptoSharia UI** - shared design system and component library

## Platform-Level Principles

- API-first backbone: app repos consume CryptoSharia API as central business/data contract source.
- BFF-first security: protected API calls run server-side in each SvelteKit app.
- Unified identity: auth and user lifecycle are centralized through Accounts/API.
- Contract discipline: app-side BFF responses are stable, UI-shaped, and safe.
- Cross-app consistency: shared trust and UX expectations across ecosystem products.

## Brainstorming Guardrails

When the user asks for product/business ideas:

- Prioritize trust and educational outcomes over speculative growth tactics.
- Prefer low-risk experiments with explicit assumptions and success metrics.
- Keep ideas feasible within SvelteKit + BFF + centralized API architecture.

Avoid:

- Overstating compliance certainty.
- Advice that implies guaranteed financial outcomes.
- Proposals that weaken trust boundaries, auth, or security posture.
