# revoke-github-token-action

Revoke an installation access token using GitHub Apps for GitHub Actions.

<!-- actdocs start -->

## Description

This action revokes a specified GitHub App installation access token.
Although these tokens automatically expire after one hour, manual revocation enhances security.

To prevent workflow failures, this action **always succeeds**,
even if the token is already revoked or an error occurs.
All errors are ignored, allowing workflows to continue running smoothly.
See the [FAQ](#what-happens-if-the-token-is-already-invalid) for more details on this behavior.

## Usage

```yaml
  steps:
    - name: Revoke GitHub Token
      uses: tmknom/revoke-github-token-action@v0
      with:
        token: <your-github-installation-access-token>
```

## Inputs

| Name | Description | Default | Required |
| :--- | :---------- | :------ | :------: |
| token | GitHub App installation access token. | n/a | yes |

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
