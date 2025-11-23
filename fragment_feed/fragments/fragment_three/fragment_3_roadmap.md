Fragment 3: The Roadmap

Date: November 23, 2025
Context: This document outlines the Capability Maturity Model for the Fragment Protocol ecosystem.

Abstract

Rather than a linear timeline, the Fragment Protocol is defined by "Levels of Capability." This allows developers to build Agents ranging from simple, read-only scripts to complex, automated aggregators.

Level 0: Raw (Bootstrapped)

The "Read-Only" Shim.
At this level, an Agent treats a Fragment simply as a directory of files. It relies on the user to provide the URL.

Capabilities:

Access a Fragment via URL.

Parse the fragment.json Manifest to find the Source text.

Render the Source text to the user.

Security Protocol:

Trust State: UNVERIFIED.

User Warning: The Agent MUST inform the user: "I have loaded this content, but I cannot verify its authenticity. Signatures have not been checked."

Commercial/Ownership: It must display the ownership block information as plain text.

Level 1: Diet (The "Lite" Reader)

The Verification Assistant.
An Agent that adds basic checks to prevent low-effort phishing, suitable for lightweight implementations or browser extensions.

Capabilities:

Feed Following: Can check a fragment_feed.json for updates.

Expression Support: Can load standard HTML/PDF expressions provided by the publisher.

Security Protocol:

Contextual Verification: The Agent checks if the URL of the public key matches the domain claiming to be the publisher.

Check: If publisher_domain is "nytimes.com", the Agent validates that the key is fetched from nytimes.com/.well-known/....

Flag: If the key URL does not match the claimed domain, the Agent generates a Security Red Flag.

Level 2: Full Fat (The Standard Browser)

The Guardian of Trust.
The standard for a dedicated Fragment User Agent. It automates the entire Chain of Trust.

Capabilities:

Cryptographic Verification: Performs the full RSA-SHA256 handshake for both Publisher and Author signatures.

Trust Library: Maintains a local, private database of trusted keys/domains (e.g., "Always trust fragments signed by Jane Doe"). Note: This library is not shareable to prevent social engineering.

Presentation Engine: Fully supports the presentation block, adapting the content style based on the Author's intent and User's local preferences.

Security Protocol:

Strict Enforcement: Content with broken signatures is rejected by default.

Level 3: Publisher (The Forge)

The Creation Toolchain.
This is not usually the Reader Agent itself, but an external tool or software suite with built-in LLM capabilities used to generate Fragments.

Capabilities:

Authoring: Interfaces with file systems (GitHub, Google Drive) to ingest raw drafts.

Key Management: Securely holds the Author's Private Key to sign Source files.

Feed Management: Automatically updates the fragment_feed.json when a new Fragment is published.

Security Protocol:

Air-Gapped Signing: Ideally, the signing mechanism is isolated from the generation mechanism to prevent AI hallucinations from leaking private keys.

Level 4: Aggregator (The Curator)

The Bundle Engine.
A sophisticated system designed to discover, package, and redistribute content.

Capabilities:

Multi-Feed Synthesis: Combines content from multiple Publisher feeds into a new thematic collection.

Expression Generation: Can auto-generate new Expressions (e.g., creating an audio summary of a text-only fragment) and append them to the bundle.

Security Protocol:

The Bundle Signature: Introduces a third layer of trust.

Source Signature: (Signed by Author) - Immutable.

Fragment Signature: (Signed by Original Publisher) - Verifies the original package.

Bundle Signature: (Signed by Aggregator) - Verifies the collection.

Ownership Preservation: The Agent MUST preserve the ownership blocks of all original sources.

Future Development Priorities

Standardise Level 1: Release a reference implementation for a "Lite" JavaScript reader.

Level 4 Spec: Draft the schema extension required for "Bundle Signatures."