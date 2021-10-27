<!--
  _____   ____    _   _  ____ _______   ______ _____ _____ _______ 
 |  __ \ / __ \  | \ | |/ __ \__   __| |  ____|  __ \_   _|__   __|
 | |  | | |  | | |  \| | |  | | | |    | |__  | |  | || |    | |   
 | |  | | |  | | | . ` | |  | | | |    |  __| | |  | || |    | |   
 | |__| | |__| | | |\  | |__| | | |    | |____| |__| || |_   | |   
 |_____/ \____/  |_| \_|\____/  |_|    |______|_____/_____|  |_|   

This file is auto-generated by script/update-agent-help.sh, please update the
agent CLI help in https://github.com/buildkite/agent and run the generation
script.

-->

### Usage

`buildkite-agent artifact search [options] <query>`

### Description

Searches for build artifacts specified by &lt;query> on Buildkite

Note: You need to ensure that your search query is surrounded by quotes if
using a wild card as the built-in shell path globbing will provide files,
which will break the search.

### Example

    $ buildkite-agent artifact search "pkg/*.tar.gz" --build xxx

This will search across all uploaded artifacts in a build for files that match that query.
The first argument is the search query.

If you're trying to find a specific file, and there are multiple artifacts from different
jobs, you can target the particular job you want to search the artifacts from using --step:

    $ buildkite-agent artifact search "pkg/*.tar.gz" --step "tests" --build xxx

You can also use the step's job id (provided by the environment variable $BUILDKITE_JOB_ID)

Output formatting can be altered with the -format flag as follows:

    $ buildkite-agent artifact search "*" -format "%p\n"

The above will return a list of filenames separated by newline.

### Options

* `--step value` - Scope the search to a particular step by using either its name or job ID
* `--build value` - The build that the artifacts were uploaded to [`$BUILDKITE_BUILD_ID`]
* `--include-retried-jobs` - Include artifacts from retried jobs in the search [`$BUILDKITE_AGENT_INCLUDE_RETRIED_JOBS`]
* `--format value` - Output formatting of results. Defaults to "%j %p %c\n" (Job ID, path, created at time).

The following directives are available:

%i    UUID of the artifact

%p    Artifact path

%c    Artifact creation time (an ISO 8601 / RFC-3339 formatted UTC timestamp)

%j    UUID of the job that uploaded the artifact, helpful for subsequent artifact downloads

%s    File size of the artifact in bytes

%S    SHA1 checksum of the artifact

%u    Download URL for the artifact, though consider using 'buildkite-agent artifact download' instead
(default: "%j %p %c\n")
* `--agent-access-token value` - The access token used to identify the agent [`$BUILDKITE_AGENT_ACCESS_TOKEN`]
* `--endpoint value` - The Agent API endpoint (default: "`https://agent.buildkite.com/v3`") [`$BUILDKITE_AGENT_ENDPOINT`]
* `--no-http2` - Disable HTTP2 when communicating with the Agent API. [`$BUILDKITE_NO_HTTP2`]
* `--debug-http` - Enable HTTP debug mode, which dumps all request and response bodies to the log [`$BUILDKITE_AGENT_DEBUG_HTTP`]
* `--no-color` - Don't show colors in logging [`$BUILDKITE_AGENT_NO_COLOR`]
* `--debug` - Enable debug mode [`$BUILDKITE_AGENT_DEBUG`]
* `--experiment value` - Enable experimental features within the buildkite-agent [`$BUILDKITE_AGENT_EXPERIMENT`]
* `--profile value` - Enable a profiling mode, either cpu, memory, mutex or block [`$BUILDKITE_AGENT_PROFILE`]
