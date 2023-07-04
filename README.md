# shopify-theme-preview

Creates/Updates a Shopify theme to the respective tore and adds the preview link within the PR description and also as a comment.

The workflow is triggered when a Pull Request is both opened and any additional commits are made to the branch.

## Variables Setup

| Secret                  | Description                                          | Required | Type    |
| ----------------------- | ---------------------------------------------------- | -------- | ------- |
| SHOPIFY_FLAG_STORE      | The Shopify store URL e.g. store-name.myshopify.com  | true     | String  |
| SHOPIFY_CLI_THEME_TOKEN | The Shopify CLI theme token created via a custom app | true     | Number  |
| BUILD_PRODUCTION        | Assumes there is a script named: "build:production"  | optional | Boolean |

### SHOPIFY_FLAG_STORE

### SHOPIFY_CLI_THEME_TOKEN

### BUILD_PRODUCTION

Usually, when you are building a shopify theme locally, you will have made local edits via a pull request and then wish to compile an javascript
or any other build logic prior to theme deployment. There is an optional flag named `BUILD_PRODUCTION` which if set to `true` will look for a script command within the `package.json` file and execute just before a shopify theme is created/updated.

## Usage

```
steps:
  - uses: Jay-Plumb/shopify-theme-preview@1.0.2
    with:
      shopify-flag-store: ${{ env.SHOPIFY_FLAG_STORE }}
      shopify-cli-theme-token: ${{ env.SHOPIFY_CLI_THEME_TOKEN }}
      build-production: ${{ env.BUILD_PRODUCTION }}
```
