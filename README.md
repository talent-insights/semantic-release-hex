# semantic-release-hex

> [**semantic-release**](https://github.com/semantic-release/semantic-release) plugin to publish a [hex](https://hex.pm) package

[![Latest Version](https://img.shields.io/npm/v/semantic-release-hex/latest.svg?logo=npm)](https://www.npmjs.com/package/semantic-release-hex)
[![Next Version](https://img.shields.io/npm/v/semantic-release-hex/next.svg?logo=npm)](https://www.npmjs.com/package/semantic-release-hex)
[![Build](https://img.shields.io/github/actions/workflow/status/talent-ideal/semantic-release-hex/release.yml?logo=github)](https://github.com/talent-ideal/semantic-release-hex/actions/workflows/release.yml)
[![CodeQL](https://img.shields.io/github/actions/workflow/status/talent-ideal/semantic-release-hex/codeql.yml?logo=github&label=CodeQL)](https://github.com/talent-ideal/semantic-release-hex/actions/workflows/codeql.yml)
[![Coverage](https://img.shields.io/sonar/coverage/Talent-Ideal_semantic-release-hex?logo=sonarcloud&server=https%3A%2F%2Fsonarcloud.io)](https://sonarcloud.io/summary/overall?id=Talent-Ideal_semantic-release-hex)
[![OpenSSF Scorecard](https://img.shields.io/ossf-scorecard/github.com/talent-ideal/semantic-release-hex?label=openssf%20scorecard)
](https://securityscorecards.dev/viewer/?uri=github.com/talent-ideal/semantic-release-hex)
[![Discord](https://img.shields.io/discord/1158414767770308648?logo=discord)](https://discord.gg/cRB8XRFKzH)

> **Warning**
> Publishing to `hex` has not yet been implemented, so this package only bumps the version in `mix.exs` and `README.md` for now.

| Step               | Description                                                                                              |
| ------------------ | -------------------------------------------------------------------------------------------------------- |
| `verifyConditions` | Verify the presence of the `mix.exs` file and that the version is parsable.                              |
| `prepare`          | Update the version in `mix.exs` and `README.md`.                                                         |
| _`publish`_        | _[to be implemented](https://github.com/talent-ideal/semantic-release-hex/discussions/14) (PRs welcome)_ |

## Installation

```shell
npm install semantic-release-hex -D
```

For a more detailed setup guide, see [**Setting up an existing Elixir project**](./docs/SETTING_UP.md).

## Usage

Add the plugin to the [**semantic-release** configuration file](https://github.com/semantic-release/semantic-release/blob/master/docs/usage/configuration.md#configuration) (see example below).

> **Warning**
> Make sure you put the `semantic-release-hex` plugin above `@semantic-release/git` and `@semantic-release/github`, or the updated `mix.exs` file won't be included in the commit/tag/release.

### Example

```json
{
  "plugins": [
    "@semantic-release/commit-analyzer",
    "@semantic-release/release-notes-generator",
    "@semantic-release/changelog",
    "semantic-release-hex",
    [
      "@semantic-release/git",
      {
        "assets": ["CHANGELOG.md", "mix.exs"],
        "message": "chore(release): v${nextRelease.version} [skip ci]\n\n${nextRelease.notes}"
      }
    ],
    "@semantic-release/github"
  ]
}
```

## Supported version formats

### `mix.exs`

#### Regular

```elixir
  def project do
    [
      version: "0.4.2",
    ]
  end
```

#### Module attribute

```elixir
  @version "0.4.2"

  def project do
    [
      version: @version,
    ]
  end
```

### `README.md`

````markdown
```elixir
  def deps do
    {:hello_world, "0.4.2"},
    {:hello_world, "~> 0.4.2"},
    {:hello_world, git: "https://github.com/hello_world/hello_world.git", tag: "v0.4.2"},
  end
```
````

## Community

Join the [Discord server](https://discord.gg/cRB8XRFKzH)! Here you can discuss issues and get help in a more casual forum than GitHub.

## Contributing

This project is looking for help! If you're interested in helping with the project, please take a look at our [contributing documentation](https://github.com/talent-ideal/semantic-release-hex/blob/main/CONTRIBUTING.md).

### Submitting Bugs/Issues

Please have a look at our [contributing documentation](https://github.com/talent-ideal/semantic-release-hex/blob/main/CONTRIBUTING.md), it contains all the information you need to know before submitting an issue.
