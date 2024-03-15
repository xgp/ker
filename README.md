> :bug: **This is not real (yet). This is an experiment to see how this could work.**

# Keycloak Extension Repository

This tries to solve the following problems:
- Where to find/publish Keycloak extensions
- Where to find/publish information about dependencies and version compatibility
- How to install Keycloak extensions

## Publishing extensions

Basically, it's a simple as opening a PR to `main` with a manifest file and (optionally) a README in the `repository` under your package directory (e.g. `io.phasetwo`). Assuming your manifest file is compliant and you "own" (need to define) the namespace/package, the automation does the rest.

### Manifest file format

```yaml
version: '1'

package: "com.mycompany.myplugin"
name: "My Plugin"
description: "This is my plugin"
doc-url: "https://example.com"
git-url: "https://github.com/example/plugin.git"

versions:
  0.60.1:
    keycloak: [23.0.0,23.0.7)
    artifact-url: 
    artifact-sha: 
    release-notes-url:
    git-tag: 'tag-v0.56'
    dependencies: 
      maven: 
        - 'dnsjava:dnsjava:3.5.3'
      ker:
        - 'io.phasetwo.keycloak:keycloak-events:0.22'
```

#### Definitions

Required unless specified

- `version` Manifest file version. Currently only `1`.
- `package` Approved namespace.
- `name` Extension name.
- `description` Extension description (optional).
- `doc-url` Documentation URL (optional). Can be duplicated in each version, if different.
- `scm-url` Source code URL (optional).Can be duplicated in each version, if different.
- `versions` Array of extension versions. Each is an object with version name/number as key.
  - `keycloak` Keycloak version range. E.g. `[23.0.0,23.0.7)`. Uses [standard Maven version range syntax](https://cwiki.apache.org/confluence/display/MAVENOLD/Dependency+Mediation+and+Conflict+Resolution#DependencyMediationandConflictResolution-DependencyVersionRanges). Unbounded ranges will not be accepted.
  - `artifact-url` Jar URL.
  - `artifact-sha` Jar SHA1.
  - `release-notes-url` Release notes URL (optional).
  - `scm-tag` Source control tag (optional).
  - `dependencies` Maven or KER dependencies lists in the format `<group>:<name>:<version>`. Transitive dependencies are not resolved.
    - `maven` List of Maven dependencies.
    - `ker` List of KER dependencies.


### What the validation action does, and how to read the output

#### Check/Build/Package

- Checks URLs
- Validates/Caches jar and checks SHA1

### What you get out of it

- Page on the ker site

### Installing extensions from the repository

?? Helper tools in the future
