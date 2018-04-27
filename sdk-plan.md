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

## SDK code

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
* Use single points of authority configuration files (eg. don't spread the module name throughout the codebase)

### Simplify configs

* Use a single, root `.yaml` file for all config
* Use the README.md as the app's description on KBase

### General ease-of-use

* Easy `kb-sdk` installation with a shell command like: `curl https://sh.rustup.rs -sSf | sh`
* Script generator and scaffolding commands
  * Could be in the CLI or in an online UI (Jeff's examples: [ebot](https://www.ncbi.nlm.nih.gov/Class/PowerTools/eutils/ebot/ebot.cgi) and [nersc jobscript generator](https://my.nersc.gov/script_generator.php))
  * Need to expand concrete ideas here
  * Automatic Jinja2 html report template generation 
* A `views` directory that can hoild Jinja2 templates. You could name these views in your return parameters to auto-generate html reports
* Auto-generate python param schemas and validators with cerberos
* Auto-download assembly and genome parameters to scratch if they have the right type
  * Maybe the type alone doesn't work
  * Abstract away scratch -- auto-download to a path in scratch
* Auto-generate a report based on some standard return data from the method
  * Can already do this to a limited extent
* `kb-sdk release` to publish changes
* Add a `kb-sdk shell` command
* Accept python unittest options in `kb-sdk test` (eg. for only testing a certain method)
* Add a `kb-sdk coverage` command that runs a simple http server on the test coverage directory
* Use pipenv and set up a default Pipfile to make it easy for people to add pip packages
* Debug mode / ENV variable
  * If you set the DEBUG env var (or similar) then utilites like DFU could print more or less helpful data
* General error message audit and improvement for utils like DFU 

### Misc.

* Consider setting versions in dependencies.json with wildcards (eg. to `1.2.*` or `1.*`) as the default for all installed apps.
* In app dev, always automatically pull the latest commit on master without having to re-register
* Auto-generate a README.md with ideas from common-readme: https://github.com/noffle/common-readme
* QuickCheck for apps based on KIDL specs (automatic tests based on the types)
* Use an ENV var for setting the kbase auth token (eg KBASE_TOKEN)

### Resources

* SDK presentation from jjeffryes https://docs.google.com/presentation/d/1it5n6TlUGAkUBbiex4WDebMDWtYZHTxicGFcHTvxluo/edit?usp=sharing
* jfroula's SDK feedback https://gist.github.com/jfroula/3b23194bc08903ae23fad71268007b64
* Bob and Nomi's notes: https://docs.google.com/document/d/16YTkKA6pRzEi0eWRyG6jSx_OUT8Cce-300dalPDKkJI/edit#
* JGI Meeting feedback: https://docs.google.com/document/d/1BMeH6j7-LHANrw3KPITubgI8H91JyT_S2Ne4OSXa114/edit?ts=5ad65574
