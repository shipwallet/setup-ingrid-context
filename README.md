# Setup Ingrid Context

**This is a public repository**

This repo contains the GitHub Action used to download the latest version of our custom actions.

The repository where the actions are stored is a private repository within our Organization.

This action also checkouts the repository with our application code and setups the environment variables needed for our pipelines.

## ⚠️ Version 2 (Breaking Change)

**v2** introduces a mandatory requirement for **GitHub App Authentication**.
This change was made to prevent API rate limiting and to improve security by removing shared personal access tokens (PATs).

**Requirements:**
* You must have a GitHub App installed on your repository.
* You must provide `app_id` and `app_private_key` as inputs.

---

# Usage (v2)
```yaml
- uses: shipwallet/setup-ingrid-context@v2
  with:
    # 🟢 REQUIRED: GitHub App Credentials
    app_id: ${{ secrets.CI_APP_ID }}
    app_private_key: ${{ secrets.CI_APP_PRIVATE_KEY }}

    # Path where the code should be checked out
    # Default: ingrid-actions
    path: 'ingrid-actions'

    # The branch, tag or SHA to checkout.
    # Default: master
    ref: 'master'
```

# Usage (v1)

This action uses an environment variable name `GH_TOKEN_SW_BOT` to authenticate and checkout the private repo.

<!-- start usage -->
```yaml
- uses: shipwallet/setup-ingrid-context@v1
  with:
    # Path where the code should be checked out
    # Default: ingrid-actions
    path: ''

    # The branch, tag or SHA to checkout. When checking out the repository that
    # triggered a workflow, this defaults to the reference or SHA for that event.
    # Otherwise, uses the default branch.
    ref: ''
```
<!-- end usage -->
