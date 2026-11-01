---
title: "ForgejoKit"
summary: "Use typed Forgejo repositories, issues, comments, labels, milestones, and pull requests."
category: "Overview"
order: 0
keywords: ["forgejo", "issues", "repositories", "rest", "tickets"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# ForgejoKit

ForgejoKit is a source-only synchronous Forgejo REST client for repository and ticket panels. It uses Buoy URLConnection without a command-line tool or extra native library. Models preserve their server payload as RawJSON for fields not mapped by this release.

## Connection policy

Supply the complete HTTPS API root, including api/v1 and any reverse-proxy prefix. Tokens stay in memory and travel in the Authorization token header, not in URLs or persistent settings. Applications obtain credentials from their own settings/keychain. Redirect following is disabled, TLS verification is enabled, and timeouts are finite.

Confine each stateful client to one worker; network calls block. Plain HTTP is accepted only for explicitly opted-in localhost or 127.0.0.1 test servers. There are no automatic retries.

## Supported scope

Read repository/PR metadata and list or create/update tickets and comments. OAuth, uploads, webhooks, review mutations, repository creation, issue-label mutations, and PR merging are outside the API.

## Read next

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
