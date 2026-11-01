---
title: "forgejokit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["ForgejoAPIException", "ForgejoClient", "ForgejoComment", "ForgejoIssue", "ForgejoIssuePage", "ForgejoLabel", "ForgejoLabelPage", "ForgejoMilestone", "ForgejoMilestonePage", "ForgejoPullRequest", "ForgejoPullRequestPage", "ForgejoRepository"]
dependencies: []
symbols: ["ForgejoAPIException", "ForgejoClient", "ForgejoComment", "ForgejoIssue", "ForgejoIssuePage", "ForgejoLabel", "ForgejoLabelPage", "ForgejoMilestone", "ForgejoMilestonePage", "ForgejoPullRequest", "ForgejoPullRequestPage", "ForgejoRepository"]
related: ["api.md", "getting-started.md", "index.md"]
---

# forgejokit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## ForgejoKit functions

### EncodeForgejoSegment

`Public Function EncodeForgejoSegment(value As String) As String`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `value` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `String` |

## ForgejoAPIException

`Public Class ForgejoAPIException Inherits Exception`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `HTTPStatus` | `Integer` | No | No | — | — |
| `RequestID` | `String` | No | No | — | — |
| `RateLimitRemaining` | `String` | No | No | — | — |
| `RateLimitReset` | `String` | No | No | — | — |
| `RetryAfter` | `String` | No | No | — | — |

### Constructor

`Public Sub Constructor(message As String, status As Integer, requestID As String, remaining As String, resetValue As String, retry As String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `message` | `String` | `ByVal` | Required |
| `status` | `Integer` | `ByVal` | Required |
| `requestID` | `String` | `ByVal` | Required |
| `remaining` | `String` | `ByVal` | Required |
| `resetValue` | `String` | `ByVal` | Required |
| `retry` | `String` | `ByVal` | Required |

Returns: no value.

## ForgejoRepository

`Public Class ForgejoRepository`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `RawJSON` | `JSONItem` | No | No | — | — |
| `ID` | `Integer` | No | No | — | — |
| `Name` | `String` | No | No | — | — |
| `FullName` | `String` | No | No | — | — |
| `Description` | `String` | No | No | — | — |
| `HTMLURL` | `String` | No | No | — | — |
| `DefaultBranch` | `String` | No | No | — | — |
| `IsPrivate` | `Boolean` | No | No | — | — |

### Constructor

`Public Sub Constructor(data As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `JSONItem` | `ByVal` | Required |

Returns: no value.

## ForgejoIssue

`Public Class ForgejoIssue`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `RawJSON` | `JSONItem` | No | No | — | — |
| `ID` | `Integer` | No | No | — | — |
| `Number` | `Integer` | No | No | — | — |
| `Title` | `String` | No | No | — | — |
| `Body` | `String` | No | No | — | — |
| `State` | `String` | No | No | — | — |
| `HTMLURL` | `String` | No | No | — | — |
| `CommentCount` | `Integer` | No | No | — | — |
| `IsPullRequest` | `Boolean` | No | No | — | — |

### Constructor

`Public Sub Constructor(data As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `JSONItem` | `ByVal` | Required |

Returns: no value.

## ForgejoComment

`Public Class ForgejoComment`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `RawJSON` | `JSONItem` | No | No | — | — |
| `ID` | `Integer` | No | No | — | — |
| `Body` | `String` | No | No | — | — |
| `HTMLURL` | `String` | No | No | — | — |
| `CreatedAt` | `String` | No | No | — | — |

### Constructor

`Public Sub Constructor(data As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `JSONItem` | `ByVal` | Required |

Returns: no value.

## ForgejoLabel

`Public Class ForgejoLabel`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `RawJSON` | `JSONItem` | No | No | — | — |
| `ID` | `Integer` | No | No | — | — |
| `Name` | `String` | No | No | — | — |
| `Color` | `String` | No | No | — | — |
| `Description` | `String` | No | No | — | — |

### Constructor

`Public Sub Constructor(data As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `JSONItem` | `ByVal` | Required |

Returns: no value.

## ForgejoMilestone

`Public Class ForgejoMilestone`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `RawJSON` | `JSONItem` | No | No | — | — |
| `ID` | `Integer` | No | No | — | — |
| `Title` | `String` | No | No | — | — |
| `Description` | `String` | No | No | — | — |
| `State` | `String` | No | No | — | — |
| `DueOn` | `String` | No | No | — | — |

### Constructor

`Public Sub Constructor(data As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `JSONItem` | `ByVal` | Required |

Returns: no value.

## ForgejoPullRequest

`Public Class ForgejoPullRequest`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `RawJSON` | `JSONItem` | No | No | — | — |
| `ID` | `Integer` | No | No | — | — |
| `Number` | `Integer` | No | No | — | — |
| `Title` | `String` | No | No | — | — |
| `Body` | `String` | No | No | — | — |
| `State` | `String` | No | No | — | — |
| `HTMLURL` | `String` | No | No | — | — |
| `Merged` | `Boolean` | No | No | — | — |
| `Draft` | `Boolean` | No | No | — | — |

### Constructor

`Public Sub Constructor(data As JSONItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `data` | `JSONItem` | `ByVal` | Required |

Returns: no value.

## ForgejoIssuePage

`Public Class ForgejoIssuePage`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Items` | `Array Of ForgejoIssue` | No | No | — | — |
| `Page` | `Integer` | No | No | — | — |
| `Limit` | `Integer` | No | No | — | — |
| `TotalCount` | `Integer` | No | No | `-1` | — |
| `LinkHeader` | `String` | No | No | — | — |
| `PageCount` | `Integer` | No | No | `-1` | — |
| `RawJSON` | `JSONItem` | No | No | — | — |

## ForgejoLabelPage

`Public Class ForgejoLabelPage`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Items` | `Array Of ForgejoLabel` | No | No | — | — |
| `Page` | `Integer` | No | No | — | — |
| `Limit` | `Integer` | No | No | — | — |
| `TotalCount` | `Integer` | No | No | `-1` | — |
| `LinkHeader` | `String` | No | No | — | — |
| `PageCount` | `Integer` | No | No | `-1` | — |
| `RawJSON` | `JSONItem` | No | No | — | — |

## ForgejoMilestonePage

`Public Class ForgejoMilestonePage`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Items` | `Array Of ForgejoMilestone` | No | No | — | — |
| `Page` | `Integer` | No | No | — | — |
| `Limit` | `Integer` | No | No | — | — |
| `TotalCount` | `Integer` | No | No | `-1` | — |
| `LinkHeader` | `String` | No | No | — | — |
| `PageCount` | `Integer` | No | No | `-1` | — |
| `RawJSON` | `JSONItem` | No | No | — | — |

## ForgejoPullRequestPage

`Public Class ForgejoPullRequestPage`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Items` | `Array Of ForgejoPullRequest` | No | No | — | — |
| `Page` | `Integer` | No | No | — | — |
| `Limit` | `Integer` | No | No | — | — |
| `TotalCount` | `Integer` | No | No | `-1` | — |
| `LinkHeader` | `String` | No | No | — | — |
| `PageCount` | `Integer` | No | No | `-1` | — |
| `RawJSON` | `JSONItem` | No | No | — | — |

## ForgejoClient

`Public Class ForgejoClient`

### Constructor

`Public Sub Constructor(apiBase As String, token As String = "", allowLoopbackHTTP As Boolean = False, timeoutSeconds As Integer = 30)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `apiBase` | `String` | `ByVal` | Required |
| `token` | `String` | `ByVal` | `""` |
| `allowLoopbackHTTP` | `Boolean` | `ByVal` | `False` |
| `timeoutSeconds` | `Integer` | `ByVal` | `30` |

Returns: no value.

### GetRepository

`Public Function GetRepository(owner As String, repo As String) As ForgejoRepository`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `ForgejoRepository` |

### GetIssue

`Public Function GetIssue(owner As String, repo As String, index As Integer) As ForgejoIssue`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `index` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `ForgejoIssue` |

### CreateIssue

`Public Function CreateIssue(owner As String, repo As String, title As String, body As String = "") As ForgejoIssue`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `title` | `String` | `ByVal` | Required |
| `body` | `String` | `ByVal` | `""` |

#### Returns

| Type |
| --- |
| `ForgejoIssue` |

### UpdateIssue

`Public Function UpdateIssue(owner As String, repo As String, index As Integer, changes As JSONItem) As ForgejoIssue`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `index` | `Integer` | `ByVal` | Required |
| `changes` | `JSONItem` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `ForgejoIssue` |

### ListComments

`Public Function ListComments(owner As String, repo As String, index As Integer) As Array Of ForgejoComment`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `index` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of ForgejoComment` |

### CreateComment

`Public Function CreateComment(owner As String, repo As String, index As Integer, body As String) As ForgejoComment`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `index` | `Integer` | `ByVal` | Required |
| `body` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `ForgejoComment` |

### GetPullRequest

`Public Function GetPullRequest(owner As String, repo As String, index As Integer) As ForgejoPullRequest`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `index` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `ForgejoPullRequest` |

### ListIssues

`Public Function ListIssues(owner As String, repo As String, page As Integer = 1, limit As Integer = 30, state As String = "open", issueType As String = "issues") As ForgejoIssuePage`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `page` | `Integer` | `ByVal` | `1` |
| `limit` | `Integer` | `ByVal` | `30` |
| `state` | `String` | `ByVal` | `"open"` |
| `issueType` | `String` | `ByVal` | `"issues"` |

#### Returns

| Type |
| --- |
| `ForgejoIssuePage` |

### ListLabels

`Public Function ListLabels(owner As String, repo As String, page As Integer = 1, limit As Integer = 30) As ForgejoLabelPage`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `page` | `Integer` | `ByVal` | `1` |
| `limit` | `Integer` | `ByVal` | `30` |

#### Returns

| Type |
| --- |
| `ForgejoLabelPage` |

### ListMilestones

`Public Function ListMilestones(owner As String, repo As String, page As Integer = 1, limit As Integer = 30, state As String = "open") As ForgejoMilestonePage`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `page` | `Integer` | `ByVal` | `1` |
| `limit` | `Integer` | `ByVal` | `30` |
| `state` | `String` | `ByVal` | `"open"` |

#### Returns

| Type |
| --- |
| `ForgejoMilestonePage` |

### ListPullRequests

`Public Function ListPullRequests(owner As String, repo As String, page As Integer = 1, limit As Integer = 30, state As String = "open") As ForgejoPullRequestPage`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `owner` | `String` | `ByVal` | Required |
| `repo` | `String` | `ByVal` | Required |
| `page` | `Integer` | `ByVal` | `1` |
| `limit` | `Integer` | `ByVal` | `30` |
| `state` | `String` | `ByVal` | `"open"` |

#### Returns

| Type |
| --- |
| `ForgejoPullRequestPage` |
