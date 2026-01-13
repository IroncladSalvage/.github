### Welcome to Ironclad Salvage

**We keep the code compiling so you don't have to.**

We act as a **software salvage yard** for abandoned-but-essential software, operating on a strict ethos of "Minimal Viable Maintenance." We do not add features. We do not refactor for elegance. We do not answer support tickets. Our mission is singular: prevent total bit-rot.

We utilize aggressive automation, dependency bots, and CI pipelines to ensure that valuable legacy tools can still run on modern architectures (amd64, arm64), modern runtimes (supported Python, Node), and LTS operating systems.

> *If it compiles, ships, and doesn't segfault... our job is done.*

### What to expect

We operate differently than standard open source projects. We are **preservationists**, not developers.

* **❌ No New Features:** Please do not submit PRs that add functionality. They will be closed.
* **✅ The "Bandaid" Rule:** If you can fix a breakage with a one-line config change instead of a refactor, do the one-line change. We may not accept the refactor.
* **✅ Security Second:** We prioritize running software more than CVE patches and critical dependency bumps. But it is still high on our list.
* **✅ CI Fixes:** If the build is red on the `master` branch, we accept a patch to make it green.

### Our Plan

* **Automated Dependency Management:** Set up bots on forks of OSS projects to automatically bump dependencies, fix version conflicts, and open PRs only when something breaks compatibility or has a critical security issue.
* **Security Patching:** Scan for CVEs periodically and apply the smallest possible patch or pin to a safe version—no feature work, just stop it from being a liability.
* **CI-Only Testing & Builds:** Run lightweight CI pipelines that test against the latest stable runtimes (Python, Node, Java, Go, etc.) and fail loudly if it breaks. Auto-build and cache artifacts (binaries, wheels, containers) so users can grab working versions without compiling themselves.
* **Docker / Container Refresh**: Maintain minimal Dockerfiles that layer the old code on the latest base images (e.g., alpine:latest, debian:trixie), publish updated images to GitHub Containers on a schedule or when base OS updates.
* **Distro Packaging:** Keep simple packages alive for Debian and Ubuntu LTS releases or Alpine main support release.
* **Runtime Porting:** Quick patches for widely available architectures (amd64 and arm64 only) and drop support for less mainstream architectures (armv7, i686).
* **Linux only:** Let's be honest. You do not deploy code with anything else.
* **Documentation Auto-Updates**: Minimal README tweaks: add badges for current build status, one-line install commands for modern tools, or a "known working versions" table (Python 3.11+, Node 20+, etc.).
* **Automated Releases:** Tag and release new versions with a timestamp.

Ultra-low commitment: forks only get touched when automation fails or something critically breaks. It’s more "life support" than "full revival." 

### Projects we take on

We are picky scavengers. We do not want to maintain the entire internet. We generally accept:

* **Defunct projects** that have no clear, active drop-in replacement.
* **Archived repositories** or dead organizations that still have high utility.
* **Projects we like** (purely subjective maintainer bias).

**For Burned-out Maintainers:**
If you are done with your project and want to walk away without much guilt, you are welcome to bring it here *if* we see the value. We won't nurture it, but it may breathe a little longer.

**For Desperate Users:**
**Look elsewhere first.** If there is an active fork, a rewrite in Rust, or a better modern alternative, prioritize that. This is a hospice, possibly the last resort.

### What can go wrong

**We rely entirely on GitHub's free tier for public repositories.**

Our salvage operation exist only because the infrastructure currently costs us nothing. We heavily utilize:

1. **GitHub Actions** (Standard Runners) to power our CI pipelines.
2. **GitHub Container Registry (GHCR)** to host our Docker images.
3. **Actions Artifacts** to store build outputs.

**If these stop being free, we will immediately cease that part of the process: Updating software, publishing images or artifacts**
