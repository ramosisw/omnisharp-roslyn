omnisharp-roslyn
================

[![Build Status](https://dev.azure.com/omnisharp/Builds/_apis/build/status/OmniSharp.omnisharp-roslyn?branchName=master)](https://dev.azure.com/omnisharp/Builds/_build/latest?definitionId=2&branchName=master)

## Introduction

OmniSharp is a .NET development platform based on [Roslyn](https://github.com/dotnet/roslyn) workspaces. It provides project dependencies and C# language services to various IDEs and plugins.

OmniSharp is built with the [.NET Core SDK](https://dot.net/) on Windows and [Mono](http://www.mono-project.com/) on OSX/Linux. It targets the *net472* target framework. For platforms other than Windows, OmniSharp ships with an *embedded Mono* which is based on version *5.18.0* and provisioned during the build script. If *Mono* is globally installed on the system, OmniSharp will prefer it over the embedded version, however version *>=5.18.0* is required.

For Arch Linux users, you need package [msbuild-stable](https://aur.archlinux.org/packages/msbuild-stable/) (>= 16.0).

In addition, if you need the HTTP interface and you want to run on Linux, you'll also need to make sure that you have [libuv](http://libuv.org) installed. See also https://github.com/OmniSharp/omnisharp-roslyn/issues/1202#issuecomment-421543905 .

## What's new

See our [change log](https://github.com/OmniSharp/omnisharp-roslyn/blob/master/CHANGELOG.md) for all of the updates.

## Using OmniSharp

OmniSharp ships in two flavors:

* Stdio server
* HTTP server 

### Prerelease Versions
Pre-release versions are available in azure storage, they can be viewed [here](https://roslynomnisharp.blob.core.windows.net/releases?restype=container&comp=list).

All changes to `master` will be pushed to this feed and will be made available with the following convention:
`https://roslynomnisharp.blob.core.windows.net/releases/{version}/{packagename}-{os/arch}.{ext}`

* Version is auto incremented and is visible in the travis or appveyor build output
* Package Name would be either `omnisharp` or `omnisharp.http`
* `os/arch` will be one of the following:
  * `win-x64`
  * `win-x86`
  * `linux-x64`
  * `linux-x86`
  * `osx`
  * `mono`  (Requires global mono installed)
* Extensions are archive specific, windows will be `zip` and all others will be `tar.gz`.

### Building

**On Windows**:

```
> ./build.ps1
```

**On Linux / Unix**:

```
$ ./build.sh
```

You can find the output under `artifacts/publish/OmniSharp/<runtime id>/<target framework>/`.

The executable is either `OmniSharp.exe` or `OmniSharp`.

For more details, see [Build](https://github.com/OmniSharp/omnisharp-roslyn/blob/master/BUILD.md).

### VS Code

Add the following setting to your [User Settings or Workspace Settings](https://code.visualstudio.com/Docs/customization/userandworkspace).

``` JSON
{
  "omnisharp.path": "<Path to the omnisharp executable>"
}
```

The above option can also be set to:
* "latest" - To consume the latest build from the master branch
* A specific version number like `1.29.2-beta.60`

In order to be able to attach a debugger, add the following setting:

```JSON
{
  "omnisharp.waitForDebugger": true
}
```

This will print the OmniSharp process ID in the VS Code OmniSharp output panel and pause the start of the server until a debugger is attached to this process. This is equivalent to launching OmniSharp from a command line with the `--debug` flag.

### Configuration

OmniSharp provides a rich set of hierarchical configuration options, controlled via startup arguments, environment variables and `omnisharp.json` file. For more details please visit the [Configuration Options](https://github.com/OmniSharp/omnisharp-roslyn/wiki/Configuration-Options) section of the wiki.

## Help wanted!

We have slack room as well. [Get yourself invited](https://omnisharp.herokuapp.com/): [here](https://omnisharp.herokuapp.com/)

