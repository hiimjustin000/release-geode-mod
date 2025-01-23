# release-geode-mod
A GitHub action that releases a new version of a mod for Geode, a Geometry Dash mod loader.

## Usage
```yml
name: Release Geode Mod

on:
  workflow_dispatch:

jobs:
  release:
    name: Release mod
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: hiimjustin000/release-geode-mod@main
        with:
          # The GitHub token to use for the release.
          token: ${{ secrets.GITHUB_TOKEN }}
          # The path to the mod's directory. Defaults to the current directory.
          path: ./
          # Whether or not to replace an existing release. Defaults to false.
          replace: false
          # Whether or not to create a draft release. Defaults to false.
          draft: false
          # Whether or not to create a pre-release. Defaults to false.
          prerelease: false

  publish:
    name: Publish mod
    runs-on: ubuntu-latest
    needs: ['release']

    steps:
      - uses: actions/checkout@v4

      - uses: hiimjustin000/release-geode-mod/publish@main
        with:
          # The GitHub token to use for the release.
          token: ${{ secrets.GITHUB_TOKEN }}
          # The path to the mod's directory. Defaults to the current directory.
          path: ./
```

## Example
An example workflow that builds and releases a mod can be found [here](./examples/release.yml).

## License
This project is licensed under the [MIT License](./LICENSE).