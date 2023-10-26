# actions

[![codespell.yml](https://github.com/winstxnhdw/actions/actions/workflows/codespell.yml/badge.svg)](https://github.com/winstxnhdw/actions/actions/workflows/codespell.yml)
[![dependabot.yml](https://github.com/winstxnhdw/actions/actions/workflows/dependabot-public.yml/badge.svg)](https://github.com/winstxnhdw/actions/actions/workflows/dependabot-public.yml)

This repository contains a collection of my reusable GitHub workflows. Most actions are handwritten for performance, except for officially maintained actions.

## Workflows

- [bun.yml](#bunyml)
- [codespell.yml](#codespellyml)
- [dependabot-private.yml](#dependabot-privateyml)
- [dependabot-public.yml](#dependabot-publicyml)
- [docker-push.yml](#docker-pushyml)
- [format-bun.yml](#format-bunyml)
- [format-python.yml](#format-pythonyml)
- [keep-alive.yml](#keep-aliveyml)
- [python.yml](#pythonyml)
- [release.yml](#releaseyml)
- [renovate-public.yml](#renovate-publicyml)
- [spaces-deploy.yml](#spaces-deployyml)
- [spaces-restart.yml](#spaces-restartyml)
- [spaces-warmer.yml](#spaces-warmeryml)

### bun.yml

Reusable [Bun](https://github.com/oven-sh/bun) [workflow](.github/workflows/bun.yml) for lint/test/build.

```yml
jobs:
  bun:
    uses: winstxnhdw/actions/.github/workflows/bun.yml@main
    with:
      disable-test: false
      disable-build: false
      build-args: --test
```

Minimally, you can use it in the following manner.

```yml
jobs:
  bun:
    uses: winstxnhdw/actions/.github/workflows/bun.yml@main
```

### codespell.yml

Reusable [codespell](https://github.com/codespell-project/codespell) [workflow](.github/workflows/codespell.yml) for checking misspelled words in source code.

```yml
jobs:
  codespell:
    uses: winstxnhdw/actions/.github/workflows/codespell.yml@main
    with:
      path: /
      skip: ''
```

Minimally, you can use it in the following manner.

```yml
jobs:
  codespell:
    uses: winstxnhdw/actions/.github/workflows/codespell.yml@main
    with:
      path: /
```

### dependabot-private.yml

Reusable [Dependabot](https://github.com/dependabot/dependabot-core) [workflow](.github/workflows/dependabot-private.yml) for auto-merging Dependabot pull requests in private repositories.

```yml
permissions:
  contents: write
  pull-requests: write

jobs:
  auto-merge:
    uses: winstxnhdw/actions/.github/workflows/dependabot-private.yml@main
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

### dependabot-public.yml

Reusable [Dependabot](https://github.com/dependabot/dependabot-core) [workflow](.github/workflows/dependabot-public.yml) for auto-merging Dependabot pull requests in public repositories.

```yml
permissions:
  contents: write

jobs:
  auto-merge:
    uses: winstxnhdw/actions/.github/workflows/dependabot-public.yml@main
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

### docker-push.yml

Reusable [Docker](https://github.com/docker/build-push-action) [workflow](.github/workflows/docker-push.yml) for pushing Docker images into the GitHub Container registry.

```yml
permissions:
  packages: write

jobs:
  build:
    uses: winstxnhdw/actions/.github/workflows/docker-push.yml@main
    with:
      file: Dockerfile.build
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

### format-bun.yml

Reusable [Bun](https://github.com/oven-sh/bun) [workflow](.github/workflows/format-bun.yml) for fixing Bun formatting and lints with [Prettier](https://github.com/prettier/prettier) and [ESLint](https://github.com/eslint/eslint).

```yml
permissions:
  contents: write

jobs:
  format:
    uses: winstxnhdw/actions/.github/workflows/format-bun.yml@main
```

### format-python.yml

Reusable [Python](https://github.com/python/cpython) [workflow](.github/workflows/format-python.yml) for fixing Python formatting with [ruff](https://github.com/astral-sh/ruff).

```yml
permissions:
  contents: write

jobs:
  format:
    uses: winstxnhdw/actions/.github/workflows/format-python.yml@main
```

### keep-alive.yml

Reusable [workflow](.github/workflows/keep-alive.yml) for keeping your GitHub workflows alive. GitHub suspends workflows after 60 days of inactivity. Learn more [here](https://docs.github.com/en/actions/using-workflows/disabling-and-enabling-a-workflow).

```yml
name: Keep Alive

on:
  schedule:
    #       ┌──────────────── minute (0 - 59)
    #       │ ┌────────────── hour (0 - 23)
    #       │ │ ┌──────────── day of the month (1 - 31)
    #       │ │ │ ┌────────── month (1 - 12 or JAN-DEC)
    #       │ │ │ │ ┌──────── day of the week (0 - 6 or SUN-SAT)
    #       │ │ │ │ │
    #       │ │ │ │ │
    #       │ │ │ │ │
    #       * * * * *
    - cron: 0 0 1 * *

permissions:
  contents: write

jobs:
  keep-alive:
    uses: winstxnhdw/actions/.github/workflows/keep-alive.yml@main
```

### python.yml

Reusable [Python](https://github.com/python/cpython) [workflow](.github/workflows/python.yml) for lint/test/build with [Poetry](https://github.com/python-poetry/poetry), [Pylint](https://github.com/pylint-dev/pylint) and [Pyright](https://github.com/microsoft/pyright).

```yml
jobs:
  python:
    uses: winstxnhdw/actions/.github/workflows/python.yml@main
    with:
      python-version: '*'
      disable-test: false
```

Minimally, you can use it in the following manner.

```yml
jobs:
  python:
    uses: winstxnhdw/actions/.github/workflows/python.yml@main
```

### release.yml

Reusable [workflow](.github/workflows/release.yml) for naively uploading a releases to GitHub from a workflow artifact.

```yml
permissions:
  contents: write

jobs:
  release:
    uses: winstxnhdw/actions/.github/workflows/release.yml@main
    with:
      release-tag: latest
      release-title: Build
      release-asset: dist/*
      artifact-name: build
      artifact-path: dist/
```

### renovate-public.yml

Reusable [Renovate](https://github.com/renovatebot/renovate) [workflow](.github/workflows/renovate-public.yml) for auto-merging Renovate pull requests in public repositories.

```yml
permissions:
  contents: write

jobs:
  auto-merge:
    uses: winstxnhdw/actions/.github/workflows/renovate-public.yml@main
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

### spaces-deploy.yml

Reusable [Hugging Face Spaces](https://huggingface.co/docs/hub/spaces-overview) [workflow](.github/workflows/spaces-deploy.yml) for deploying a `Dockerfile` to a Hugging Face Space of the same repository name.

```yml
jobs:
  deploy:
    uses: winstxnhdw/actions/.github/workflows/spaces-deploy.yml@main
    secrets:
      token: ${{ secrets.HF_TOKEN }}
```

### spaces-restart.yml

Reusable [Hugging Face Spaces](https://huggingface.co/docs/hub/spaces-overview) [workflow](.github/workflows/spaces-restart.yml) for factory restarting a Hugging Face Space of the same repository name.

```yml
jobs:
  restart:
    uses: winstxnhdw/actions/.github/workflows/spaces-restart.yml@main
    secrets:
      token: ${{ secrets.HF_TOKEN }}
```

### spaces-warmer.yml

Reusable [Hugging Face Spaces](https://huggingface.co/docs/hub/spaces-overview) [workflow](.github/workflows/spaces-warmer.yml) for warming a Hugging Face Space of the same repository name.

```yml
name: Warm

on:
  schedule:
    #       ┌──────────────── minute (0 - 59)
    #       │ ┌────────────── hour (0 - 23)
    #       │ │ ┌──────────── day of the month (1 - 31)
    #       │ │ │   ┌──────── month (1 - 12 or JAN-DEC)
    #       │ │ │   │ ┌────── day of the week (0 - 6 or SUN-SAT)
    #       │ │ │   │ │
    #       │ │ │   │ │
    #       │ │ │   │ │
    #       * * *   * *
    - cron: 0 0 */2 * *

jobs:
  warm:
    uses: winstxnhdw/actions/.github/workflows/spaces-warmer.yml@main
```
