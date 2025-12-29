# Some things to test manually

Running the build workflow separately:

 - It is possible to run with universe ""
 - It is possible to run with universe that is empty.
 - Works for pull requests.

Things to test about workflow runs in a monorepo:

 - The _maintainer field contains the UUID if available
 - Slack message when deploy fails.
 - Reverse deps get triggered when version is bumped.
 - BiocCheck automatically runs for bioc and bioc-release.
 - Ropensci deploys docs and jobs results include pkgdown success.
 - Packages from remotes have _registered=false and do not get aritcles and webpage.
 - Failed source builds get a failure upload.

If there is an app:

 - Commit status is set if app is installed,
 - Commit status is set pending during build.
 - Commit status is failure if source/release/devel fails.
 - Commit status is success if build was cancelled due to newer run.
 - For ropensci, commit status repots docs success separately

Organization specific things:

 - Registry metadata is copied from registry (e.g. for ropensci reviewed packages).
 - Biocondcutor packages have '_bioccheck' field.
 - Upstream branch name is stored in RemoteRef (e.g. ropensci packages).
 - GitHub codesearch count is stored in _searchresults field.
 - The CRAN_VERSION envvar is propagated everywhere for multiverse.
