# bazel-registry

A static [Bazel module registry](https://bazel.build/external/registry)
serving [hello_build](https://github.com/altdansalt/hello-build) releases.

Consume it by adding to your workspace's `.bazelrc`:

```
common --registry=https://raw.githubusercontent.com/altdansalt/bazel-registry/main
common --registry=https://bcr.bazel.build
```

then in MODULE.bazel:

```python
bazel_dep(name = "hello_build", version = "<latest in modules/hello_build>")
```

Entries are published by `release.sh` in the hello-build repo; each
source.json points at a `git archive` tarball attached to a GitHub
release (stable artifact, sha256 in `integrity`).
