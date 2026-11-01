# Access Forgejo repositories, issues and pull requests

A source-only, cross-platform Forgejo REST client for an IDE's repository and
issue panels. `Import forgejokit` exposes typed repositories, issues, comments,
labels, milestones and pull-request metadata. Every entity also preserves its
server payload in `RawJSON` for fields not mapped by this release.

The client uses Buoy's native `URLConnection`, so it adds no native library or
command-line tool dependency. Requests block the calling thread; use a worker
thread in a GUI. Client instances are stateful and should not be shared between
concurrent requests.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add forgejokit --git https://github.com/BuoyBay/forgejokit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```buoy
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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer forgejokit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

The generated agent files and editor settings stay local and are ignored by Git.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
