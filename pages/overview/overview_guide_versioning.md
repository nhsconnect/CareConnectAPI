---
title: Guide Versioning
keywords: development, versioning
tags: [development]
sidebar: overview_sidebar
permalink: overview_guide_versioning.html
summary: An overview of this implementation guide is versioned.
---

{% include important.html content="This site is under active development by NHS Digital on behalf of INTEROPen and is intended to provide all the technical resources you need to successfully develop the Care Connect APIs. This project is being developed using an agile methodology so iterative updates to content will be added on a regular basis." %}

## Alpha ##

This implementation guide is in currently in an alpha state at the moment. This means that changes and releases are occuring regularly.

### Semantic Versioning ###

Given a version number MAJOR.MINOR.PATCH, increment the:

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards-compatible manner, and
- PATCH version when you make backwards-compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

A pre-release version MAY be denoted by appending a hyphen (refer to [Semantic Versioning - Item 9](http://semver.org/#spec-item-9){:target="_blank"})

For examples: 1.0.0-alpha.1 is a valid pre-release version.

### Pre-release Labels ###

The following pre-release labels will be used across all products:

| Pre-release Label | Lifecycle | Description |
|-------------------|-----------|-------------|
| `alpha` | &nbsp; | Complete enough for internal testing. |
| `beta` | early | Complete enough for external testing. |
| `beta` | late | Complete enough for external testing. Usually feature complete. |
| `rc` | &nbsp; | Almost ready for final release. No new feature enhancements. |

> rc = Release Candidate. 

