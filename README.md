> :bug: **This is not real (yet). This is an experiment to see how this could work.**

# Keycloak Extension Repository

This tries to solve the following problems:
- Where to find/publish Keycloak extensions
- Where to find/publish information about dependencies and version compatibility
- How to install Keycloak extensions

## Publishing extensions

Basically, it's a simple as opening a PR to `main` with your manifest file in the `repository` under your package directory (e.g. `io.phasetwo`). Assuming your manifest file is compliant and you "own" (need to define) the namespace/package, the automation does the rest.

### Manifest file format

```yaml
mf-version: '1'

namespace: 'io.phasetwo.keycloak'
extension: 'keycloak-orgs'
version: '0.56'

dependencies: 
  maven: 
    - 'dnsjava:dnsjava:3.5.3'
  ker:
    - 'io.phasetwo.keycloak:keycloak-events:0.22'

keycloak-versions:
  
```

### What the validation action does, and how to read the output

#### Check

- built agains the correct version of Keycloak

#### Build/package


### What you get out of it

- Page on the ker site
- Jar(s) in the repo


## Installing extensions from the repository

