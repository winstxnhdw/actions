# actions

This repository contains a collection of my reusable GitHub workflows. Most custom actions are handwritten for performance, except for officially maintained actions.

## Workflows

### bun.yml

Reusable [Bun](https://github.com/oven-sh/bun) [workflow](.github/workflows/bun.yml) for lint/test/build.

```yml
jobs:
  bun:
    uses: winstxnhdw/actions/.github/workflows/bun.yml@main
    with:
      disable-test: false
      disable-build: false
      build-args: false
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
jobs:
  auto-merge:
    uses: winstxnhdw/actions/.github/workflows/dependabot-private.yml@main
```

### dependabot-public.yml

Reusable [Dependabot](https://github.com/dependabot/dependabot-core) [workflow](.github/workflows/dependabot-public.yml) for auto-merging Dependabot pull requests in public repositories.

```yml
jobs:
  auto-merge:
    uses: winstxnhdw/actions/.github/workflows/dependabot-public.yml@main
```

### docker-push.yml

Reusable [Docker](https://github.com/docker/build-push-action) [workflow](.github/workflows/docker-push.yml) for pushing Docker images into the GitHub Container registry.

```yml
jobs:
  build:
    uses: winstxnhdw/actions/.github/workflows/docker-push.yml@main
```

### format-python.yml

Reusable [Python](https://github.com/python/cpython) [workflow](.github/workflows/format-python.yml) for fixing Python formatting with [isort](https://github.com/PyCQA/isort).

```yml
jobs:
  format:
    uses: winstxnhdw/actions/.github/workflows/format-python.yml@main
```

### python.yml

Reusable [Python](https://github.com/python/cpython) [workflow](.github/workflows/python.yml) for lint/test/build with [Poetry](https://github.com/python-poetry/poetry), [Pylint](https://github.com/pylint-dev/pylint) and [Pyright](https://github.com/microsoft/pyright).

```yml
jobs:
  python:
    uses: winstxnhdw/actions/.github/workflows/python.yml@main
    with:
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

### spaces-deploy.yml

Reusable [Hugging Face Spaces](https://huggingface.co/docs/hub/spaces-overview) [workflow](.github/workflows/spaces-deploy.yml) for deploying a `Dockerfile` to a Hugging Face Space of the same repository name.

```yml
jobs:
  deploy:
    uses: winstxnhdw/actions/.github/workflows/spaces-deploy.yml@main
```

### spaces-restart.yml

Reusable [Hugging Face Spaces](https://huggingface.co/docs/hub/spaces-overview) [workflow](.github/workflows/spaces-restart.yml) for factory restarting a Hugging Face Space of the same repository name.

```yml
jobs:
  restart:
    uses: winstxnhdw/actions/.github/workflows/spaces-restart.yml@main
```

### spaces-warmer.yml

Reusable [Hugging Face Spaces](https://huggingface.co/docs/hub/spaces-overview) [workflow](.github/workflows/spaces-warmer.yml) for warming a Hugging Face Space of the same repository name.

```yml
jobs:
  restart:
    uses: winstxnhdw/actions/.github/workflows/spaces-warmer.yml@main
```
