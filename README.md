# setup-dotnet

This action sets up a dotnet environment for use in actions by:

- optionally downloading and caching a version of dotnet by version and adding to PATH
- registering problem matchers for error output

# Usage

See [action.yml](action.yml)

Basic:
```yaml
steps:
- uses: actions/checkout@master
- uses: actions/setup-dotnet@v1
  with:
    version: 2.2.103 // Version to use.
- run: dotnet build <my project>
```

Matrix Testing:
```yaml
jobs:
  build:
    strategy:
      matrix:
        dotnet: [ 2.2.103, 3.5.2, 4.5.1 ]
    name: Dotnet ${{ matrix.dotnet }} sample
    steps:
      - uses: actions/checkout@master
      - name: Setup dotnet
        uses: actions/setup-dotnet@v1
        with:
          version: ${{ matrix.dotnet }}
      - run: dotnet build <my project>
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)

# Contributions

Contributions are welcome!  See [Contributor's Guide](docs/contributors.md)
