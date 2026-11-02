---
title: "ForgejoKit getting started"
summary: "Install and use ForgejoKit with explicit configuration and resource ownership."
category: "Guides"
order: 10
keywords: ["forgejo", "issues", "repositories", "rest", "tickets"]
related: ["index.md", "api.md", "typed-api.md"]
---

# ForgejoKit getting started

Copy the forgejokit archive to packages and import it. Replace the illustrative API root, owner, and repository before running. The example reads the first page of public tickets anonymously; use your application's credential provider when authentication is required.

```basic
Import forgejokit

Sub Main()
    Dim client As New ForgejoClient("https://forgejo.example.org/api/v1")
    Try
        Dim page As ForgejoIssuePage = client.ListIssues("team", "project")
        For Each issue As ForgejoIssue In page.Items
            Print issue.Title
        Next
    Catch e As ForgejoAPIException
        Print e.Message
    End Try
End Sub
```

## Paging and identifiers

List calls request one page with a limit of 1 through 100. Forgejo can impose a smaller limit. Read TotalCount and PageCount when available; -1 means the server omitted a count header. LinkHeader is preserved and never followed automatically.

Issue Number is the repository-local route index. ID is a separate global object identity and must not be substituted for Number. Default ListIssues requests issues rather than pull requests. ListComments follows the endpoint's unpaged contract.

## Updates and errors

UpdateIssue accepts only explicitly supplied fields in a nonempty JSON object. Omitted fields remain untouched; an empty body is a deliberate update. Catch ForgejoAPIException for response metadata. Transport failures have status zero; rate limits and write operations are not retried automatically.

## Read next

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
