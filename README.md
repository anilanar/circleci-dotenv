# anilanar/dotenv

Reuse .env files in your repo by sourcing them and making them available in your environment as environment variables. You can also check the [registry page](https://circleci.com/orbs/registry/orb/anilanar/dotenv).

## Usage

1. Use CircleCI version 2.1 at the top of your .circleci/config.yml file.

```yaml
version: 2.1
```

2. Add the orbs stanza below your version, invoking the orb:

```yaml
orbs:
  dotenv: anilanar/dotenv@1.0.0
```

3. Use `dotenv/source` as a step:

```yaml
steps:
  - dotenv/source:
      path: .ci.env
```

## Example

```yaml
version: 2.1
orbs:
  dotenv: anilanar/dotenv@volatile
jobs:
  build:
    docker:
      - image: 'circleci/node:8.17'
    working_directory: ~/repo
    steps:
      - checkout
      - dotenv/source:
          path: .env
      - run: make build
```
