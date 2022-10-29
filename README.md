# commons-workflow

[![MIT LICENSE](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

Too Long, Goto [TL;DR](#tldr)

A reusable git actions workflow
----

## Github Actions Workflow
Well this is a long story, but all you need to configure the settings.xml on github actions workfow.
The simplest solution will be to do this, please check [`maven-central`](../maven-central)

`build.yml`

Build and test on pull request, with test coverage report
```yaml
name: Build and Test

on:
  pull_request:
    types: [ opened, reopened, synchronize ]
    branches: [ master, main ]

jobs:
  build:
    uses: deelaa-marketplace/commons-workflow/.github/workflows/build-test.yml@main
    secrets: inherit
```

`publish-api.yml`

Publish open-api specs package to [`maven-central`](../maven-central) as a .zip
```yaml
name: Publish API Specification

on:
  push:
    branches: [ master, main ]
    paths:
      - 'src/main/resources/api-specification/**'

jobs:
  publish:
    uses: deelaa-marketplace/commons-workflow/.github/workflows/publish-api.yml@main
    secrets: inherit
```

`publish.yml`

Publish and package artifact to [`maven-central`](../maven-central) mostly as .jar
```yaml
name: Publish

on:
  release:
    types: [ published ]
    branches: [ "master","main" ]

jobs:
  publish:
    uses: deelaa-marketplace/commons-workflow/.github/workflows/publish-package.yml@main
    secrets: inherit
```

###  TL;DR
Sample: [order-service](../order-service)

## License

[MIT](https://opensource.org/licenses/MIT) © [Oluwaseun Ogunjimi](). Released under the MIT license. 
