# SDK improvement

Disclaimer: Much of these ideas are unfinalized maybes.

## Docs

* Dedicated docs repo and website with Sphinx
  * Move SDK app dev docs out of kb_sdk and into separate repo
    * Easier PR turnaround
  * Expand tutorial to use a different example that modifies Dockerfile and generates report files
  * Continue to clean up and expand How-to collection
  * More working examples
  * Expand overview test, graphics, and visualizations
* Wiki (?)
  * Github wiki
  * accessibility for non-devs
* Filled-out README.md's for all apps with example apps -- (esp. reused apps)

## SDK code

### Test speed improvement

* Persist docker containers between tests
* Cache or re-use downloaded data
* Simple report and output object preview utilities

### Codebase cleanup

* Gitignore all auto-generated code that is not meant to be edited and silo it in /build. Could have `kb-sdk make` to generate /build.
* Use PyPi-hosted, versioned KBase pip packages for utilities
* Continue to auto-generate configs (eg. `travis.yml`) as part of `kb-sdk init`
* Example files that can be moved into /build or into pip packages:
  * /scripts and /test_local
  * authclient, baseclient, `*Client.py`, & java servers
  * Test class setup code
  * Makefile

### Simplify configs

* Use a single, root `.yaml` file for all config
* Use the README.md as the app's descriptionra

### General ease-of-use

* Script generator
  * One input, one output (?)
  * Need to expand concrete ideas here
* Auto-download assembly and genome parameters to scratch if they have the right type
  * Maybe the type alone doesn't work
  * Abstract away scratch -- auto-download to a path in scratch
* Auto-generate a report based on some standard return data from the method
  * Can already do this to a limited extent
* Easy `kb-sdk` installation with a shell command like: `curl https://sh.rustup.rs -sSf | sh`
* `kb-sdk release` to publish changes
* Add a `kb-sdk shell` command
* Accept python unittest options in `kb-sdk test` (eg. for only testing a certain method)
* Automatic Jinja2 html report template generation 
* Add a `kb-sdk coverage` command that runs a simple http server on the test coverage directory
* Use pipenv and set up a default Pipfile

### Misc.

* Consider setting versions in dependencies.json with wildcards (eg. to 1.2.* or 1.*) as the default for all installed apps.
* In app dev, always automatically pull the latest commit on master without having to re-register
* For docs, use inspiration from common-readme: https://github.com/noffle/common-readme
* QuickCheck for apps based on KIDL specs (automatic tests based on the types)
