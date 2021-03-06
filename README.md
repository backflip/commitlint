# [Get Started](https://conventional-changelog.github.io/commitlint/#/?id=getting-started) | [Let's chat][12] ![slack][11] | [Website](https://conventional-changelog.github.io/commitlint)

> Lint commit messages

<p align="center">
  <img width="600" src="docs/assets/commitlint.svg">
</p>

> Demo generated with [svg-term-cli](https://github.com/marionebl/svg-term-cli)
>
> `cat docs/assets/commitlint.json | svg-term --out docs/assets/commitlint.svg --frame --profile=Seti --height=20 --width=80`

[![npm latest][2]][3] [![CircleCI][4]][5] <!-- [![TravisCI][6]][7] -->

- 🚓 Be a good `commitizen`
- 📦 Share configuration via `npm`
- 🤖 Tap into `conventional-changelog`

## Contents

- [What is commitlint](#what-is-commitlint)
  - [Benefits using commitlint](#benefits-using-commitlint)
- [Getting started](#getting-started)
- [CLI](#cli)
- [Config](#config)
- [Shared configuration](#shared-configuration)
- [API](#api)
- [Tools](#tools)
- [Roadmap](#roadmap)
- [Version Support](#version-support)
- [Related projects](#related-projects)
- [License](#license)
- [Development](#development)
  - [Install and run](#install-and-run)
  - [Publishing a release](#publishing-a-release)

---

## What is commitlint

commitlint checks if your commit messages meet the [conventional commit format](https://conventionalcommits.org).

In general the pattern mostly looks like this:

```sh
type(scope?): subject  #scope is optional; multiple scopes are supported (current delimiter options: "/", "\" and ",")
```

Real world examples can look like this:

```
chore: run tests on travis ci
```

```
fix(server): send cors headers
```

```
feat(blog): add comment section
```

Common types according to [commitlint-config-conventional (based on the Angular convention)](https://github.com/conventional-changelog/commitlint/tree/master/@commitlint/config-conventional#type-enum) can be:

- build
- ci
- chore
- docs
- feat
- fix
- perf
- refactor
- revert
- style
- test

These can be modified by [your own configuration](#config).

### Benefits using commitlint

- [Why Use Conventional Commits?](https://www.conventionalcommits.org/en/v1.0.0-beta.2/#why-use-conventional-commits)
- ["The perks of committing with conventions" (Talk slides)](https://slides.com/marionebl/the-perks-of-committing-with-conventions#/)

## Getting started

```sh
# Install commitlint cli and conventional config
npm install --save-dev @commitlint/{config-conventional,cli}
# For Windows:
npm install --save-dev @commitlint/config-conventional @commitlint/cli

# Configure commitlint to use conventional config
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

To lint commits before they are created you can use Husky's `commit-msg` hook:

```sh
# Install Husky v5
npm install husky --save-dev
# or
yarn add husky --dev

# Active hooks
npx husky install
# or
yarn husky install

# Add hook
npx husky add .husky/commit-msg "npx --no-install commitlint --edit $1"
# or
yarn husky add .husky/commit-msg "yarn commitlint --edit $1"
```

If the file `.husky/commit-msg` already exists, you can edit the file and put this:

```sh
# .husky/commit-msg
# ...
npx --no-install commitlint --edit $1
# or
yarn commitlint --edit $1
```

**Detailed Setup instructions**

- [Local setup](https://conventional-changelog.github.io/commitlint/#/guides-local-setup) - Lint messages on commit with husky
- [CI setup](https://conventional-changelog.github.io/commitlint/#/guides-ci-setup) - Lint messages during CI builds

## CLI

- Primary way to interact with commitlint.
- `npm install --save-dev @commitlint/cli`
- Packages: [cli](./@commitlint/cli)

## Config

- Configuration is picked up from `commitlint.config.js`, `.commitlintrc.js`, `.commitlintrc.json`, or `.commitlintrc.yml` file or a `commitlint` field in `package.json`
- Packages: [cli](./@commitlint/cli), [core](./@commitlint/core)
- See [Rules](./docs/reference-rules.md) for a complete list of possible rules
- An example configuration can be found at [@commitlint/config-conventional](./@commitlint/config-conventional/index.js)

## Shared configuration

A number of shared configurations are available to install and use with `commitlint`:

- [@commitlint/config-angular](./@commitlint/config-angular)
- [@commitlint/config-conventional](./@commitlint/config-conventional)
- [@commitlint/config-lerna-scopes](./@commitlint/config-lerna-scopes)
- [@commitlint/config-patternplate](./@commitlint/config-patternplate)
- [conventional-changelog-lint-config-atom](https://github.com/erikmueller/conventional-changelog-lint-config-atom)
- [conventional-changelog-lint-config-canonical](https://github.com/gajus/conventional-changelog-lint-config-canonical)
- [commitlint-config-jira](https://github.com/Gherciu/commitlint-jira)

> ⚠️ If you want to publish your own shareable config then make sure it has a name aligning with the pattern `commitlint-config-emoji-log` or `commitlint-config-your-config-name` — then in extend all you have to write is `emoji-log` or `your-config-name`.

## API

- Alternative, programmatic way to interact with `commitlint`
- Packages:
  - [format](./@commitlint/format) - Format commitlint reports
  - [lint](./@commitlint/lint) - Lint a string against commitlint rules
  - [load](./@commitlint/load) - Load shared commitlint configuration
  - [read](./@commitlint/read) - Read commit messages from a specified range or last edit
- See [API](./docs/reference-api.md) for a complete list of methods and examples

## Tools

- [commitizen adapter](./@commitlint/prompt)
- [prompt](./@commitlint/prompt-cli)

## Roadmap

> **Ideas**: [conventional-changelog/commitlint#94](https://github.com/conventional-changelog/commitlint/issues/94)

`commitlint` is considered stable and is used in various projects as development tool.

We identify **ease of adoption** and **developer experience** as fields where there
is room and need for improvement. The items on the roadmap should enhance `commitlint` regarding those aspects.

- [x] **Adoption**: Provide reusable Travis CI integration: `@commitlint/travis-cli` (https://github.com/conventional-changelog/commitlint/releases/tag/v5.1.0)
- [ ] **DX**: Support PR squash scenario via [ahmed-taj/commitlint-bot](https://github.com/ahmed-taj/commitlint-bot/) and `@commitlint/travis-cli`
- [ ] **Adoption**: Make [ahmed-taj/commitlint-bot](https://github.com/ahmed-taj/commitlint-bot/) configurable via `commitlint` configuration
- [ ] **Adoption**: Create `commitlint init`
- [ ] **DX**: Extend the configuration schema to allow for additional fields (descriptions, examples, fixes) on both the rule and value level
- [ ] **DX**: Incorporate an extended version of [lennym/commit-template](https://github.com/lennym/commit-template) deducing a template from commitlint configuration
- [ ] **DX**: Rewrite `@commitlint/prompt` for better usability (might involve a lot of yak-shaving)

## Version Support

- Node.js [LTS](https://github.com/nodejs/LTS#lts-schedule) `>= 10.21.0`
- git `>= 2.13.2`

## Related projects

- [conventional-changelog](https://git.io/v18sw) – Generate a changelog from conventional commit history
- [commitizen](https://git.io/vwTym) – Simple commit conventions for internet citizens
- [create-semantic-module](https://git.io/vFjFg) – CLI for quickly integrating commitizen and commitlint in new or existing projects

## License

Copyright by @marionebl. All `commitlint` packages are released under the MIT license.

## Development

`commitlint` is developed in a mono repository.

### Install and run

```sh
git clone git@github.com:conventional-changelog/commitlint.git
cd commitlint
yarn
yarn run build # run build tasks
yarn start # run tests, again on change
```

For more information on how to contribute please take a look at our [contribution guide](./.github/CONTRIBUTING.md).

### Package dependency overview

![commitlint-dependencies](https://user-images.githubusercontent.com/4248851/58385093-34b79780-7feb-11e9-8f27-bffc4aca3eba.png)

### Publishing a release

Before publishing a release do a `yarn run publish --dry-run` to get the upcoming version and update the version
in the [`should print help` test](https://github.com/conventional-changelog/commitlint/blob/master/@commitlint/cli/src/cli.test.ts#L431).  
Commit that change before creating the new version without `--dry-run`.

```sh
npm login
```

```sh
yarn clean
yarn install
yarn run build
yarn test
yarn run publish --otp <one-time password>
```

#### Publish a `next` release

```sh
npm login
```

```sh
yarn clean
yarn install
yarn run build
yarn test
npx lerna publish --conventional-commits --dist-tag next --otp <one-time password>
```

If for some reason this stops in between, you can manually publish missing packages like this:

```
npm publish <package-name> --tag next --otp <one-time password>
```

##### Move `next` to `latest`

```sh
npm login
```

```sh
npx lerna exec --no-bail --no-private --no-sort --stream -- '[ -n "$(npm v . dist-tags.next)" ] && npm dist-tag add ${LERNA_PACKAGE_NAME}@$(npm v . dist-tags.next) latest --otp <one-time password>'
```

Remove next:

```sh
npx lerna exec --no-bail --no-private --no-sort --stream -- '[ -n "$(npm v . dist-tags.next)" ] && npm dist-tag rm ${LERNA_PACKAGE_NAME} next --otp <one-time password>'
```

[0]: https://img.shields.io/badge/stability-stable-green.svg?style=flat-square
[1]: https://nodejs.org/api/documentation.html#documentation_stability_index
[2]: https://img.shields.io/npm/v/@commitlint/cli.svg?style=flat-square
[3]: https://npmjs.org/package/@commitlint/cli
[4]: https://img.shields.io/circleci/project/github/conventional-changelog/commitlint/master.svg?style=flat-square
[5]: https://circleci.com/gh/conventional-changelog/commitlint

<!-- [6]: https://img.shields.io/appveyor/ci/conventional-changelog/commitlint/master.svg?style=flat-square
[7]: https://ci.appveyor.com/project/conventional-changelog/commitlint -->

[8]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[9]: https://nodejs.org/api/documentation.html#documentation_stability_index
[10]: https://img.shields.io/npm/v/@commitlint/cli/next.svg?style=flat-square
[11]: https://devtoolscommunity.herokuapp.com/badge.svg?style=flat-square
[12]: https://devtoolscommunity.herokuapp.com
