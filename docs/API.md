# ForgejoKit · 0.1.0

A source-only, cross-platform Forgejo REST client for an IDE's repository and
issue panels. `Import forgejokit` exposes typed repositories, issues, comments,
labels, milestones and pull-request metadata. Every entity also preserves its
server payload in `RawJSON` for fields not mapped by this release.

The client uses Buoy's native `URLConnection`, so it adds no native library or
command-line tool dependency. Requests block the calling thread; use a worker
thread in a GUI. Client instances are stateful and should not be shared between
concurrent requests.

## Build and verify

```sh
# Test a preassembled archive instead:
```

The runner seals `packages/forgejokit-0.1.0.buipkg`, copies it to `dist/`, checks
the module, test and example on all six Buoy targets, and runs a sealed consumer
against a loopback HTTP fixture. It tests encoded Unicode paths, exact request
headers and JSON payloads, issue ID/index differences, paging headers, HTTP
errors, token redaction, redirect refusal and input validation. It does not
access a real Forgejo account or create real tickets.

Copy the archive into a consumer project's `packages/` directory. The
[console example](../examples/forgejokit_demo.bui) reads public issues without
credentials. The API has no built-in credential storage: applications can obtain
a token from their own settings/keychain and supply it to the constructor.

## Client

`New ForgejoClient(apiBase, token = "", allowLoopbackHTTP = False,
timeoutSeconds = 30)` takes the complete API root, such as
`https://forgejo.example.org/api/v1` or
`https://forgejo.example.org/forge/api/v1` for a subpath installation. A trailing
slash is accepted. The base must use HTTPS and must not contain user info,
query, fragment, percent escapes, backslashes, control characters or traversal
segments. Hosts use ASCII DNS names or IPv4, with an optional numeric port;
IPv6 literals and Unicode host names are not exposed in this release. HTTP is accepted only for `localhost` or `127.0.0.1` when explicitly
opted in, for local fixtures. TLS certificate verification stays enabled.

Tokens are held in the client and sent only in the `Authorization: token ...`
header. They are not persisted, placed in URLs or logged. Redirects are disabled,
including same-host redirects: a 3xx response throws instead of forwarding an
Authorization header. Timeout and connection timeout are finite and apply to
every request. Owner and repository values are encoded as individual UTF-8 URL
segments; empty names, `.`/`..` and control characters reject before sending.

| Method | Return type / behavior |
| --- | --- |
| `GetRepository(owner, repo)` | `ForgejoRepository` with ID, name/full name, description, URL, default branch and private flag |
| `GetIssue(owner, repo, index)` | `ForgejoIssue` with ID, number, title, body, state, URL, comment count and PR marker |
| `ListIssues(owner, repo, page = 1, limit = 30, state = "open", issueType = "issues")` | `ForgejoIssuePage`; state is `open`/`closed`/`all`, type is `issues`/`pulls` |
| `CreateIssue(owner, repo, title, body = "")` | Create a ticket; returns `ForgejoIssue` |
| `UpdateIssue(owner, repo, index, changes)` | PATCH only the supplied JSON fields; returns `ForgejoIssue` |
| `ListComments(owner, repo, index)` | `Array Of ForgejoComment` |
| `CreateComment(owner, repo, index, body)` | `ForgejoComment` |
| `ListLabels(owner, repo, page = 1, limit = 30)` | `ForgejoLabelPage` with label IDs, names, colors and descriptions |
| `ListMilestones(owner, repo, page = 1, limit = 30, state = "open")` | `ForgejoMilestonePage` with milestone IDs, titles, states and due dates |
| `GetPullRequest(owner, repo, index)` | `ForgejoPullRequest` with ID/number/title/body/state/URL/draft/merged metadata |
| `ListPullRequests(owner, repo, page = 1, limit = 30, state = "open")` | `ForgejoPullRequestPage` |

Issue `Number` is the repository-local index used in routes; `ID` is a distinct
global identifier. Passing `ID` as `index` is incorrect. A Forgejo issue can
represent a pull request; `IsPullRequest` exposes that distinction. The default
list explicitly requests `type=issues`, so a ticket panel does not silently mix
pull requests into its list.

`UpdateIssue` accepts a nonempty `JSONItem` object with only `title`, `body`,
`state`, `assignees`, `milestone`, `ref`, `due_date` and `unset_due_date` fields.
`state` must be `open` or `closed`; other field validation remains with Forgejo.
The JSON is sent without filling in omitted fields, so an empty body can be set
without overwriting the title. Milestones are numeric IDs in this API.

Pages contain `Items`, `Page`, `Limit`, `TotalCount`, `PageCount`, `LinkHeader`
and `RawJSON`. Count fields are `-1` when the server omits the corresponding
`X-Total-Count`/`X-PageCount` headers. `LinkHeader` is preserved without following
it automatically. Explicit limits are restricted to 1–100; a server may impose
a smaller limit. The official comments-list endpoint has no page/limit
parameters, so `ListComments` deliberately exposes its unpaged contract.

## Errors and limits

`ForgejoAPIException` carries `HTTPStatus`, `RequestID`, `RateLimitRemaining`,
`RateLimitReset` and `RetryAfter`. Its message includes a JSON API error message
when available and redacts the configured token if a server echoes it. Transport
errors use status zero and a generic message; malformed successful JSON produces
an exception. Networking failures, rate limits and write requests are never
retried automatically, avoiding accidental duplicate ticket/comment creation.
Missing or wrongly typed optional entity fields use empty/zero/false defaults;
a top-level non-object entity or non-array list rejects.

This release does not implement OAuth, attachment upload, webhook handling,
review mutations, issue-label mutations, repository creation or PR merging.
The `RawJSON` property is a mutable snapshot and does not write anything back to
the server. Buoy's JSON number representation uses Double, so numeric IDs above
2^53 are outside this wrapper's exact-integer contract.

The implementation was checked against Forgejo's official
[API usage documentation](https://forgejo.org/docs/latest/user/api/usage/) and
[instance OpenAPI schema](https://code.forgejo.org/swagger.v1.json). Forgejo
maintains compatibility within a major version, while major releases can change
endpoints; consult the target instance's own `/swagger.v1.json` for extensions.

Test suites and fixtures are maintainer-local and are not part of this public repository.
