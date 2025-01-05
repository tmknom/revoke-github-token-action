# revoke-github-token-action

Revoke an installation access token using GitHub Apps for GitHub Actions.

<!-- actdocs start -->

## Description

This action revokes a specified GitHub Apps installation access token.
While installation access tokens automatically expire after one hour, this action allows you to revoke them immediately for enhanced security.
To ensure uninterrupted workflows, this action is designed to succeed even if an error occurs during execution.

## Usage

```yaml
  steps:
    - name: Revoke GitHub Token
      uses: tmknom/revoke-github-token-action@v0
      with:
        token: <your-gitHub-installation-access-token>
```

## Inputs

| Name | Description | Default | Required |
| :--- | :---------- | :------ | :------: |
| token | GitHub installation access token. | n/a | yes |

## Outputs

N/A

<!-- actdocs end -->

## Permissions

N/A

## FAQ

N/A

## Related projects

- [generate-github-token-action](https://github.com/tmknom/generate-github-token-action): Generate an installation access token using GitHub Apps for GitHub Actions.
- [private-generate-github-token-action](https://github.com/tmknom/private-generate-github-token-action): Generate an installation access token for personal use.

## Release notes

See [GitHub Releases][releases].

[releases]: https://github.com/tmknom/revoke-github-token-action/releases
