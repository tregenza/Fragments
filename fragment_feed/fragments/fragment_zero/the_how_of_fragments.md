The How of Fragments

Date: November 21, 2025

Abstract

While "The Zen of Fragments" defines the philosophy, this document outlines the operational ecosystem. It details how Fragments are created, distributed, discovered, and monetised in a decentralised environment.

1. The Lifecycle of a Fragment

The journey of a Fragment consists of five stages, emphasising the separation of Author and Publisher:

Creation: The Author writes in clean, semantic formats (Markdown). They do not worry about CSS or responsive design.

Source Signing: The Author cryptographically signs the raw source file. This creates an immutable "Source of Truth" that can be passed between publishers without alteration.

Packaging: The Publisher (who may be the author or a third-party aggregator) creates the Manifest. They bundle the signed Source with high-level Presentation guidance and links to any available Expressions.

Manifest Signing: The Publisher signs the JSON Manifest. This vouches for the package as a whole ("We trust this author, and we curated this content").

Consumption: A user's AI Agent discovers the Fragment. It validates the Publisher's Signature on the manifest and, optionally, the Author's Signature on the source content to ensure a complete Chain of Trust.

2. Distribution & Discovery

To avoid "Walled Gardens" and platform lock-in, discovery follows the open RSS model. Each publisher lists available fragments which 3rd parties can access. This allows for direct Publisher -> User connections as well as Publishers -> Aggregators -> User approaches.

2.1 The Fragment Feed

Publishers maintain a fragment_feed.json file at a known location.

Aggregators: Specialised AI bots which scrape publishers and present algorithm-driven lists.

Personal Agents: Users subscribe directly to publishers (e.g., "Hey Agent, follow Jane Doe's feed"). The Agent checks the feed periodically for new content.

3. The Economic Social Contract

The Fragment Protocol rejects DRM. It is impossible to force an AI to display an advertisement against its will (or its user's will). Instead, we rely on a structured Social Contract.

3.1 The Signed Commercial Block

The Commercial Block is cryptographically bound to the Source, not just the Manifest. This ensures that the economic path always leads back to the creator, regardless of who distributes the content.

Immutable Terms: The Author defines the attribution and payment pointers alongside the source text.

Signature Binding: These terms are included in the data payload signed by the Author.

Anti-Stripping: If a third-party Aggregator repackages the Source but attempts to replace the payment pointer with their own, the Author's signature will fail validation. The User Agent will detect this tampering and reject the Fragment as inauthentic.

3.2 User Agent Behaviour

We operate on the assumption that as AI Agents become trusted extensions of the user, users will configure their Agents to support creators they value.

Scenario: A user sets their Agent to "Auto-tip £0.01 to any provider in my whitelist."

Scenario: A user asks, "Is this article from a subscriber source?" The Agent checks the subscription_validation_url defined in the Fragment.