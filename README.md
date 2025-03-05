# Setup Atun GitHub Action

This GitHub Action installs the [Atun](https://github.com/automationd/atun) CLI tool, which allows you to seamlessly access your private VPC resources on AWS without needing a VPN.

## Features

- Installs Atun CLI tool
- Supports all major platforms (Linux, macOS, Windows)
- Supports all major architectures (amd64, arm64)
- Automatically adds to PATH
- Automatic latest stable version detection
- Version selection via input or environment variable
- Provides path to installed binary as output

## Usage

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: automationd/action-setup-atun@v1
  - name: Use Atun
    run: |
      # The binary is now available in PATH
      atun --version
      
      # Or use the output path
      ${{ steps.install.outputs.atun-path }} --version
```

### Specifying a Version

If you need a specific version, you can specify it using the `version` input:

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: automationd/action-setup-atun@v1
    with:
      version: '0.4.5'
```

## Inputs

| Name | Description | Required | Default |
|------|-------------|----------|---------|
| `version` | Version of Atun to install | No | 'latest' (automatically fetches latest stable release) |

## Outputs

| Name | Description |
|------|-------------|
| `atun-path` | Path to the installed Atun binary |

## Environment Variables

| Name | Description |
|------|-------------|
| `ATUN_VERSION` | Version to use when version input is set to 'latest' |

## License

MIT

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. 