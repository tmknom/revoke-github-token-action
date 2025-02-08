# revoke-github-token-action

Revoke a GitHub App installation access token in GitHub Actions.

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
      if: ${{ always() }}
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

This action does not require any additional `GITHUB_TOKEN` permissions.

## Why

GitHub App installation access tokens grant scoped permissions for automation and remain valid until they expire.
However, immediate revocation may be necessary in certain scenarios, such as:

- Reducing the window of exposure after token use
- Preventing unauthorized access if a token is leaked
- Complying with security policies that mandate explicit revocation

This action provides a straightforward way to programmatically revoke tokens,
enhancing security in automated workflows.

## FAQ

### When should I use this action?

Use this action whenever you need to revoke a GitHub App installation access token before it expires.
It is particularly useful in security-sensitive workflows where minimizing token lifetime is crucial.

### Will revoking the token affect my workflow execution?

Yes.
Any subsequent steps requiring authentication with the revoked token will fail, including:

- API requests using the token for authentication
- GitHub Actions steps that depend on this token for permissions
- Any third-party tools or scripts relying on the token

Ensure all necessary API calls are completed before revoking the token.

### What happens if the token is already invalid?

This action always succeeds, even if the token is already invalid or a GitHub API error occurs.
Failing the workflow in such cases provides little benefit because:

- If revocation fails due to a temporary GitHub API issue, the token will still expire automatically within an hour.
- Retrying is usually ineffective, as API outages cannot be resolved within the workflow.
- Keeping the workflow running is preferable since failure does not enhance security or provide a recovery method.

### Does this action affect `GITHUB_TOKEN`?

No.
This action does not impact `GITHUB_TOKEN`, which is managed separately from GitHub App installation tokens.
If you use `GITHUB_TOKEN` for `actions/checkout` or other workflows, they will continue to function as expected.

### Does this action support personal access tokens (PATs)?

No.
This action is specifically designed for GitHub App installation access tokens.
PATs require different revocation methods, which are not covered here.

## Related Projects

- [generate-github-token-action](https://github.com/tmknom/generate-github-token-action): Generates a GitHub App installation access token for GitHub Actions.
- [private-generate-github-token-action](https://github.com/tmknom/private-generate-github-token-action): Generates an installation access token for private use.

## Release Notes

See [GitHub Releases][releases].

[releases]: https://github.com/tmknom/revoke-github-token-action/releases
