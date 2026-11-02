---
title: "ForgejoKit API"
summary: "Public types, operations, error behavior, and limits for ForgejoKit."
category: "Reference"
order: 20
keywords: ["forgejo", "issues", "repositories", "rest", "tickets"]
symbols: ["ForgejoClient", "ForgejoIssue", "ForgejoRepository", "ForgejoIssuePage", "ForgejoAPIException", "ForgejoClient.ListIssues", "ForgejoClient.UpdateIssue", "EncodeForgejoSegment"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# ForgejoKit API

| API | Contract |
| --- | --- |
| ForgejoClient(apiBase, token, allowLoopbackHTTP, timeoutSeconds) | API root required; optional empty token, no HTTP opt-in, 30-second timeout. |
| GetRepository, GetIssue, GetPullRequest | Typed single-object reads. |
| ListIssues | Page/limit/state and issueType; defaults to page 1, 30 items, open issues. |
| CreateIssue, UpdateIssue | Explicit ticket creation or PATCH of supplied JSON fields. |
| ListComments, CreateComment | Unpaged comment array or newly created ForgejoComment. |
| ListLabels, ListMilestones, ListPullRequests | Typed pages with explicit paging. |
| ForgejoIssuePage, ForgejoLabelPage, ForgejoMilestonePage, ForgejoPullRequestPage | Items, Page, Limit, TotalCount, PageCount, LinkHeader, RawJSON. |
| ForgejoRepository, ForgejoIssue, ForgejoComment, ForgejoLabel, ForgejoMilestone, ForgejoPullRequest | Typed fields plus mutable RawJSON snapshot; editing a model does not write to the server. |
| EncodeForgejoSegment | Encode one validated UTF-8 path segment. |

## Failure contract

ForgejoAPIException includes HTTPStatus, RequestID, RateLimitRemaining, RateLimitReset, and RetryAfter. Messages redact the configured token. Invalid successful JSON and invalid top-level entity/list shapes reject. Missing optional model fields use empty/zero/false values.

UpdateIssue allows title, body, state, assignees, milestone, ref, due_date, and unset_due_date. State is open or closed; milestones use numeric IDs. IDs above the exact Double integer range are outside this wrapper's contract.

## Read next

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)

[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
