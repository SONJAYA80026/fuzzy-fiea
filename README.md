# GitHub Desktop Documentation

This is the [GitHub Desktop](https://github.com/desktop/desktop) development
documentation.

## Contributing

If you are interested in contributing to the project, you should read these
resources to get familiar with how things work:

 - **[How Can I Contribute?](../.github/CONTRIBUTING.md#how-can-i-contribute)** -
    details about how you can participate
 - **[Development Environment Setup](contributing/setup.md)** - everything
    you need to know to get Desktop up and running
 - **[Engineering Values](contributing/engineering-values.md)** - our high-level engineering values
 - **[Style Guide](contributing/styleguide.md)** - notes on the coding style
 - **[Tooling](contributing/tooling.md)** - if you have a preferred IDE,
    there's some enhancements to make your life easier
 - **[Troubleshooting](contributing/troubleshooting.md)** - some additional
    known issues if you're having environment issues

## Process

Details about how the team is organizing and shipping GitHub Desktop:

 - **[Roadmap](process/roadmap.md)** - the future as planned so far
 - **[Release Planning](process/release-planning.md)** - how we plan and execute
    releases
 - **[Issue Triage](process/issue-triage.md)** - how we address issues reported
    by users
 - **[Pull Requests](process/pull-requests.md)** - how code contributions are submitted and reviewed
 - **[Releasing Updates](process/releasing-updates.md)** - how we deploy things

## Technical

These documents contain more details about the internals of GitHub Desktop
and how things work:

 - **[Dialogs](technical/dialogs.md)** - details about the dialog component API
 - **[Windows menu bar](technical/windows-menu-bar.md)** - Electron doesn't
    provide inbuilt support for styling the menu for Windows, so we've created
    our own custom components to achieve this.
 - **[Developer OAuth App](technical/oauth.md)** - GitHub Desktop ships with
    the ability to OAuth on behalf of a user. A developer OAuth app is bundled
    to reduce the friction of getting started.
 - **[Building and Packaging Desktop](technical/packaging.md)** - Outlines how
    Desktop is currently packaged for all platforms 
 - **[Automatic Git Proxy support](technical/proxies.md)** - A pre-launch overview
    and troubleshooting guide for the Git automatic proxy support in GitHub Desktop.
    

## SETUP FORMAT

-- name: Setup Go environment
  uses: actions/setup-go@v2.1.3
  with:
    # The Go version to download (if necessary) and use. Supports semver spec and ranges.
    go-version: # optional
    # Whether to download only stable versions
    stable: # optional, default is true
    # Used to pull node distributions from go-versions.  Since there's a default, this is typically not supplied by the user.
    token: # optional, default is ${{ github.token }}
    
    - name: Setup Python
  uses: actions/setup-python@v2.2.2
  with:
    # Version range or exact version of a Python version to use, using SemVer's version range syntax.
    python-version: # optional, default is 3.x
    # The target architecture (x86, x64) of the Python interpreter.
    architecture: # optional
    # Used to pull python distributions from actions/python-versions. Since there's a default, this is typically not supplied by the user.
    token: # optional, default is ${{ github.token }}
    
 - name: Docker Setup Buildx
  # You may pin to the exact commit or the version.
  # uses: docker/setup-buildx-action@0d135e0c2fc0dba0729c1a47ecfcf5a3c7f8579e
  uses: docker/setup-buildx-action@v1.3.0
  with:
    # Buildx version. (eg. v0.3.0)
    version: # optional
    # Sets the builder driver to be used
    driver: # optional, default is docker-container
    # List of additional driver-specific options. (eg. image=moby/buildkit:master)
    driver-opts: # optional
    # Flags for buildkitd daemon
    buildkitd-flags: # optional, default is --allow-insecure-entitlement security.insecure --allow-insecure-entitlement network.host
    # Sets up docker build command as an alias to docker buildx
    install: # optional, default is false
    # Switch to this builder instance
    use: # optional, default is true
    # Optional address for docker socket or context from `docker context ls`
    endpoint: # optional
    # BuildKit config file
    config: # optional
    
    - name: setup-lnmp
  # You may pin to the exact commit or the version.
  # uses: khs1994-docker/actions-setup-lnmp@c1cf7e6ce769803b2db8569e3429c73466c66d28
  uses: khs1994-docker/actions-setup-lnmp@0.0.1
  with:
    # lnmp branch
    lnmp_branch: # optional, default is 19.03
    # lnmp services
    lnmp_services: # optional, default is nginx mysql php7 redis
    # LREW package
    lrew_include: # optional, default is pcit
    # docker compose version
    docker_compose_version: # optional, default is 1.24.0
    
    - name: Azure DevOps NPM
  # You may pin to the exact commit or the version.
  # uses: ponicode/azure-devops-npm-action@4053172f755545f9635d2e083514c83fb2e41a95
  uses: ponicode/azure-devops-npm-action@1.0.0
  with:
    # Your Azure organisation
    organisation: 
    # Your Azure project
    project: 
    # Your Azure registry
    registry: 
    # Your Azure user
    user: 
    # Your Azure password
    password: 
    # Your Azure email
    email: 
    # Your package scope
    scope: # optional
    
    - name: Setup Stack
  # You may pin to the exact commit or the version.
  # uses: mstksg/setup-stack@69e4283faeb7a89f26326daa36e9cc0fa7a023bd
  uses: mstksg/setup-stack@v2
  
  - name: Setup Bazel
  # You may pin to the exact commit or the version.
  # uses: abhinavsingh/setup-bazel@1fe920bf5df3791aab606c06a3608f4bb600c4f2
  uses: abhinavsingh/setup-bazel@v3
  with:
    # Bazel version to install e.g. 1.2.1, 2.0.0, ...
    version: # optional, default is 2.0.0
    
    - name: Setup MSYS2
  # You may pin to the exact commit or the version.
  # uses: msys2/setup-msys2@a43b8403533fffe0c157dd8498f021ddec66bff7
  uses: msys2/setup-msys2@v2
  with:
    # Variant of the environment to set by default: MSYS, MINGW32, MINGW64, UCRT64 or CLANG64
    msystem: # optional, default is MINGW64
    # Default value for MSYS2_PATH_TYPE environment variable: strict, inherit or minimal
    path-type: # optional, default is minimal
    # Retrieve and extract base installation from upstream GitHub Releases
    release: # optional, default is true
    # Update MSYS2 installation through pacman
    update: # optional
    # Install packages after installation through pacman
    install: # optional
    
    - name: Setup SteamCMD
  # You may pin to the exact commit or the version.
  # uses: CyberAndrii/setup-steamcmd@e19cd1516315ce46dbfffa47193f92fe42d1419e
  uses: CyberAndrii/setup-steamcmd@v1.1.1
  
  - name: Setup sampctl
  # You may pin to the exact commit or the version.
  # uses: AGraber/sampctl-action@face9c916c90b36a88f199cde81e61637727b11f
  uses: AGraber/sampctl-action@v1
  with:
    # Version of sampctl
    version: # default is 1.9.1
    
    - name: Asciidoctor Setup
  # You may pin to the exact commit or the version.
  # uses: reitzig/actions-asciidoctor@7570212ae20b63653481675fb1ff62d1073632b0
  uses: reitzig/actions-asciidoctor@v2.0.0
  with:
    # The version of asciidoctor to install.
Example: 2.0.10

    version: # optional, default is ~>2.0
