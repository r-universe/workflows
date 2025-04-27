# R-universe workflows

This repository contains the worksflows that are used to sync, build, check, and deploy R packages on [R-universe](https://r-universe.dev). This has been set up using so-called [reusable workflows](https://docs.github.com/en/actions/sharing-automations/reusing-workflows#creating-a-reusable-workflow):

The actual runs and jobs are triggered in the monorepos of the universe owner under the [r-universe](http://github.com/r-universe) GitHub organization. For example runs for `ropensci` can be found at: https://github.com/r-universe/ropensci/actions

Each of these monorepos contains a copy of the [`build.yml`](build.yml) and [`sync.yml`](sync.yml) templates from this repository. However these are mereley small wrappers which invoke the actual "reusable workflows" that you can find under [`.github/workflows`](.github/workflows) in this repository.

## The 'build' workflow

If you are here to find out how R-universe builds packages, or want to suggest changes, you are probably looking for the [`.github/workflows/build.yml`](.github/workflows/build.yml) workflow. This file contains the full process to build, check, and deploy each R package update. 

The entire process is open-source by design, and you can easily find the source for each "action" used in the workflows by navigating to the respective GitHub repository. You will find that the build workflow uses a lot of actions from the repository [r-universe-org/actions](https://github.com/r-universe-org/actions). This is where you could suggest changes to the individual steps of the build process.
