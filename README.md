# R-universe workflows

This repository contains the GHA [reusable workflows](https://docs.github.com/en/actions/sharing-automations/reusing-workflows#creating-a-reusable-workflow) that we use to sync, build, check, and deploy R packages on [R-universe](https://r-universe.dev).

For deployment to [https://r-universe.dev](https://r-universe.dev), builds are run inside the __monorepos__ of the universe owner under the [r-universe](http://github.com/r-universe) GitHub organization. For example packages from `https://ropensci.r-universe.dev` are built at: https://github.com/r-universe/ropensci/actions

## Testing the build workflow in your own GitHub repository

For debugging purposes, it is also possible to run the R-universe [`build.yml`](.github/workflows/build.yml) workflow in your own R package repository on GitHub. To test this, create a file `.github/workflows/r-universe-test.yml` in your R package source like this:

```yaml
name: Test R-universe

on:
  push:
  pull_request:

jobs:
  build:
    name: R-universe testing
    uses: r-universe-org/workflows/.github/workflows/build.yml@v3
    with:
      universe: ${{ github.repository_owner }}
```

You can either create the file manually or by calling the [`universe::use_universe_action()`](https://docs.ropensci.org/universe/reference/use_universe_action.html) function in the [universe R package](https://docs.ropensci.org/universe).

The parameter `universe` is used to set the context to a given universe. This affects where R package dependencies are downloaded from (besides the default repositories).

Triggering this workflow in your own Git repo will run exaclty the same steps as r-universe, but without deploying anything. The workflow is deliberately not customizable as it serves to test and debug the exact process as it happens on R-universe.
