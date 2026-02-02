# Setup DepotDownloader

GitHub Action that installs DepotDownloader by downloading the official release binaries and adding them to the PATH.

## Usage

Basic:

```yaml
- uses: hazre/setup-depotdownloader@v1
```

Pin a version:

```yaml
- uses: hazre/setup-depotdownloader@v1
  with:
    version: "2.7.4"
```

Use the outputs:

```yaml
- id: depotdownloader
  uses: hazre/setup-depotdownloader@v1

- run: |
    echo "DepotDownloader path: ${{ steps.depotdownloader.outputs.depotdownloader-path }}"
    echo "DepotDownloader version: ${{ steps.depotdownloader.outputs.depotdownloader-version }}"
```

## Inputs

- `version`: DepotDownloader version to install (e.g., `2.7.4` or `latest`). Default: `latest`.

## Outputs

- `depotdownloader-path`: Absolute path to the DepotDownloader executable.
- `depotdownloader-version`: The installed DepotDownloader version.

## Permissions

This action uses the GitHub CLI to download releases. If you set explicit workflow permissions, ensure `contents: read` is allowed for the job so the `GITHUB_TOKEN` can access release metadata.

## Requirements

- GitHub-hosted runners or self-hosted runners with:
  - `gh` (GitHub CLI)
  - `bash`
  - `unzip`

## How it works

The action downloads the matching asset from the SteamRE/DepotDownloader GitHub Releases page, extracts it to a temporary directory, marks the binary executable, and adds it to the PATH.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
