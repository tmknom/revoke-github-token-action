# revoke-github-token-action

Revoke an installation access token using GitHub Apps for GitHub Actions.

<!-- actdocs start -->

## Description

This action revokes a specified GitHub App installation access token.
While these tokens automatically expire after one hour, you can revoke them anytime for added security.

To prevent workflow failures, this action **always returns a successful status**,
even if the token has already been revoked or an error occurs during execution.
All errors, including GitHub API failures, are ignored to ensure workflows run smoothly.
See the [FAQ](#what-happens-if-the-token-is-already-invalid) for more details on this approach.

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
