# SDK improvement

Disclaimer: Much of these ideas are unfinalized.

## Docs

* Dedicated docs repo and website with Sphinx
  * Move SDK app dev docs out of kb_sdk and into separate repo
    * Easier PR turnaround
  * Expand tutorial to use a different example that modifies Dockerfile and generates report files
  * Continue to clean up and expand How-to collection
  * More working examples
  * Expand overview text, graphics, and visualizations
* Filled-out README.md's for all apps with example apps -- (esp. reused apps)

## SDK code improvements

Tentatively ordered by priority

_Larger changes_

* Trim down code (need guidance on details)
    * Use single points-of-authority config (eg. don't spread the module name throughout the codebase)
* Consolidate config files into single yaml
* Test speed improvements (docker persistence, network caching, report previews)
* A `views` directory that can hold Jinja2 templates. This would automatically get used in the reports.

_Smaller misc changes_

* Set all return parameters from the implementation function as options for report generation
* Use the README.md as the app's description in the catalog
* Use an ENV var for setting the kbase auth token
* Auto-generate a fuller README.md (see common-readme: https://github.com/noffle/common-readme)
* Easy `kb-sdk` installation with a shell command like: `curl https://sh.rustup.rs -sSf | sh`
* General error message improvement for app utils (human-readable with links. See this: https://docs.rs/human-panic/0.4.0/human_panic/)
* More CLI-based catalog actions, similar to package managers like `pip` or `npm` (eg. `kb-sdk release`, `kb-sdk status`)
* `kb-sdk shell` command
* `kb-sdk coverage` command that runs a simple http server on the test coverage directory
* Accept python unittest options in `kb-sdk test` (eg. for only testing a certain method)
* Log levels with an ENV variable -- increase/decrease debug messages using an env variable

_Larger maybes_

* Auto-generated run-time type checks from KIDL with python Cerberus
* QuickCheck for apps based on KIDL specs (automatic tests based on the types)
* Consider setting app versions with wildcards (eg. to `1.2.*` or `1.*`) as the default for all installed apps.

_Smaller maybes_

* Use pipenv and set up a default Pipfile to make it easy for people to add pip packages
* Automatically pre-download workspace references from params into scratch
* In app dev, always automatically pull the latest commit on master without having to re-register

## Misc. Notes

### Test speed improvement

* Persist docker containers between tests
* Cache or re-use downloaded data
* Simple report and output object preview utilities

### Codebase cleanup

* Gitignore all auto-generated code that is not meant to be edited and silo it in /build. Could have `kb-sdk make` to generate /build.
* Use PyPi-hosted, versioned KBase pip packages for utilities
  * Eg. move all the client code into a pypi package
* Continue to auto-generate configs (eg. `travis.yml`) as part of `kb-sdk init`
* Example files that can be moved into /build or into pip packages:
  * /scripts and /test_local
  * authclient, baseclient, `*Client.py`, & java servers
  * Test class setup code
  * Makefile

### General ease-of-use

* Script generator and scaffolding commands
  * Could be in the CLI or in an online UI (Jeff's examples: [ebot](https://www.ncbi.nlm.nih.gov/Class/PowerTools/eutils/ebot/ebot.cgi) and [nersc jobscript generator](https://my.nersc.gov/script_generator.php))
  * Need to expand concrete ideas here
  * Automatic Jinja2 html report template generation 
* Auto-download assembly and genome parameters to scratch if they have the right type
  * Maybe the type alone doesn't work
* (From James and Boris) Abstract away scratch (need more details)

## Resources

* SDK presentation from jjeffryes https://docs.google.com/presentation/d/1it5n6TlUGAkUBbiex4WDebMDWtYZHTxicGFcHTvxluo/edit?usp=sharing
* jfroula's SDK feedback https://gist.github.com/jfroula/3b23194bc08903ae23fad71268007b64
* Bob and Nomi's notes: https://docs.google.com/document/d/16YTkKA6pRzEi0eWRyG6jSx_OUT8Cce-300dalPDKkJI/edit#
* JGI Meeting feedback: https://docs.google.com/document/d/1BMeH6j7-LHANrw3KPITubgI8H91JyT_S2Ne4OSXa114/edit?ts=5ad65574
