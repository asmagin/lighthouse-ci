# Lighthouse CI
[![All Contributors](https://img.shields.io/badge/all_contributors-7-orange.svg?style=flat-square)](#contributors)
[![npm version](https://badge.fury.io/js/lighthouse-ci.svg)](https://badge.fury.io/js/lighthouse-ci)
[![npm](https://img.shields.io/npm/dt/lighthouse-ci.svg)](https://www.npmjs.com/package/lighthouse-ci)
[![Known Vulnerabilities](https://snyk.io/test/github/andreasonny83/lighthouse-ci/badge.svg?targetFile=package.json)](https://snyk.io/test/github/andreasonny83/lighthouse-ci?targetFile=package.json)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/xojs/xo)

> A useful wrapper around Google Lighthouse CLI

<img alt="Lighthouse CI logo" src="https://raw.githubusercontent.com/andreasonny83/lighthouse-ci/master/logo.png" width="800px">

<img src="https://raw.githubusercontent.com/andreasonny83/lighthouse-ci/master/lighthouse-cli.gif" width="700">

## Install

```
$ npm install -g lighthouse-ci
```

## Table of Contents

- [Lighthouse CI](#lighthouse-ci)
  - [Install](#install)
  - [Table of Contents](#table-of-contents)
  - [Usage](#usage)
  - [CLI](#cli)
  - [Lighthouse flags](#lighthouse-flags)
    - [Chrome flags](#chrome-flags)
  - [Configuration](#configuration)
  - [Contributors](#contributors)
  - [License](#license)

## Usage

```sh
lighthouse-ci --help
```

## CLI

```
$ lighthouse-ci --help

  Usage
    $ lighthouse-ci <target-url>

  Example
    $ lighthouse-ci https://example.com
    $ lighthouse-ci https://example.com -s
    $ lighthouse-ci https://example.com --score=75
    $ lighthouse-ci https://example.com --accessibility=90 --seo=80
    $ lighthouse-ci https://example.com --accessibility=90 --seo=80 --report=folder
    $ lighthouse-ci https://example.com --report=folder --config-path=configs.json
    $ lighthouse-ci https://example.com --audit.interaction=1000

  Options
    -s, --silent                  Run Lighthouse without printing report log
    --report=<path>               Generate an HTML report inside a specified folder
    --filename=<filename>         Specify the name of the generated HTML report file (requires --report)
    --config-path                 The path to the Lighthouse config JSON (read more here: https://github.com/GoogleChrome/lighthouse/blob/master/docs/configuration.md)
    --score=<threshold>           Specify a score threshold for the CI to pass
    --performance=<threshold>     Specify a minimal performance score for the CI to pass
    --pwa=<threshold>             Specify a minimal pwa score for the CI to pass
    --accessibility=<threshold>   Specify a minimal accessibility score for the CI to pass
    --best-practice=<threshold>   [DEPRECATED] Use best-practices instead
    --best-practices=<threshold>  Specify a minimal best-practice score for the CI to pass
    --seo=<threshold>             Specify a minimal seo score for the CI to pass
```

## Lighthouse flags

In addition to listed `lighthouse-ci` configuration flags, it is also possible to pass any native `lighthouse` flags.

To see the full list of available flags, please refer to the official [Google Lighthouse documentation](https://github.com/GoogleChrome/lighthouse#cli-options).

eg.

```sh
# Launches browser, collects artifacts, saves them to disk (in `./test-report/`) and quits
$ lighthouse-ci --gather-mode=test-report https://my.website.com
# skips browser interaction, loads artifacts from disk (in `./test-report/`), runs audits on them, generates report
$ lighthouse-ci --audit-mode=test-report https://my.website.com
```

### Chrome flags

In addition of the lighthouse flags, you can also specify extra chrome flags
comma separated.

eg.

```sh
$ lighthouse-ci --chrome-flags=--cellular-only,--force-ui-direction=rtl https://my.website.com
```

eg.

```sh
$ lighthouse-ci --emulated-form-factor desktop --seo 92 https://my.website.com
```

## Configuration

Lighthouse CI allows you to pass a custom Lighthouse configuration file.
Read [Lighthouse Configuration](https://github.com/GoogleChrome/lighthouse/blob/master/docs/configuration.md)
to learn more about the configuration options available.

Just generate your configuration file. For example this `config.json`

```json
{
  "extends": "lighthouse:default",
  "audits": [
    "user-timings",
    "critical-request-chains"
  ],

  "categories": {
    "performance": {
      "name": "Performance Metrics",
      "description": "Sample description",
      "audits": [
        {"id": "user-timings", "weight": 1},
        {"id": "critical-request-chains", "weight": 1}
      ]
    }
  }
}
```

Then run Lighthouse CI with the `--config-path` flag

```sh
$ lighthouse-ci https://example.com --report=reports --config-path=config.json
```

The generated report inside `reports` folder will follow the custom configuration listed under the `config.json` file.

## Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore -->
<table><tr><td align="center"><a href="https://about.me/andreasonny83"><img src="https://avatars0.githubusercontent.com/u/8806300?v=4" width="100px;" alt="Andrea Sonny"/><br /><sub><b>Andrea Sonny</b></sub></a><br /><a href="#question-andreasonny83" title="Answering Questions">💬</a> <a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=andreasonny83" title="Code">💻</a> <a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=andreasonny83" title="Documentation">📖</a></td><td align="center"><a href="https://snap-ci.com"><img src="https://avatars1.githubusercontent.com/u/1007970?v=4" width="100px;" alt="Celso Santa Rosa"/><br /><sub><b>Celso Santa Rosa</b></sub></a><br /><a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=celsosantarosa" title="Code">💻</a></td><td align="center"><a href="https://github.com/BenAHammond"><img src="https://avatars3.githubusercontent.com/u/3516389?v=4" width="100px;" alt="Ben Hammond"/><br /><sub><b>Ben Hammond</b></sub></a><br /><a href="https://github.com/andreasonny83/lighthouse-ci/issues?q=author%3ABenAHammond" title="Bug reports">🐛</a> <a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=BenAHammond" title="Code">💻</a></td><td align="center"><a href="https://github.com/alexecus"><img src="https://avatars1.githubusercontent.com/u/12739106?v=4" width="100px;" alt="Alex Tenepere"/><br /><sub><b>Alex Tenepere</b></sub></a><br /><a href="https://github.com/andreasonny83/lighthouse-ci/issues?q=author%3Aalexecus" title="Bug reports">🐛</a> <a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=alexecus" title="Code">💻</a></td><td align="center"><a href="https://ikigeg.com"><img src="https://avatars0.githubusercontent.com/u/8846301?v=4" width="100px;" alt="Michael Griffiths"/><br /><sub><b>Michael Griffiths</b></sub></a><br /><a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=ikigeg" title="Code">💻</a></td><td align="center"><a href="https://github.com/cmarkwell"><img src="https://avatars0.githubusercontent.com/u/23330646?v=4" width="100px;" alt="Connor Markwell"/><br /><sub><b>Connor Markwell</b></sub></a><br /><a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=cmarkwell" title="Code">💻</a></td><td align="center"><a href="https://github.com/Juuro"><img src="https://avatars2.githubusercontent.com/u/559017?v=4" width="100px;" alt="Sebastian Engel"/><br /><sub><b>Sebastian Engel</b></sub></a><br /><a href="https://github.com/andreasonny83/lighthouse-ci/issues?q=author%3AJuuro" title="Bug reports">🐛</a> <a href="https://github.com/andreasonny83/lighthouse-ci/commits?author=Juuro" title="Code">💻</a></td></tr></table>

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification. Contributions of any kind welcome!

## License

MIT

---

Created with 🦄 by [andreasonny83](https://about.me/andreasonny83)
