// Config file for automatic testing at ssbjenkins.stsci.edu

// - Copied from spacetelescope/jwql GitHub repo on 2/20/19
// - More info here: https://github.com/spacetelescope/jenkinsfile_ci_examples
// - Syntax defined here: https://github.com/spacetelescope/jenkins_shared_ci_utils

// Obtain files from source control system.
if (utils.scm_checkout()) return

// Define each build configuration, copying and overriding values as necessary.
bc0 = new BuildConfig()
bc0.nodetype = "linux-stable"
bc0.name = "debug"
bc0.build_cmds = ["conda env update --file=fgs-commissioning/environment.yml",
                  "with_env -n magic pip install fgs-commissioning/"]
bc0.test_cmds = ["with_env -n magic pytest -s --junitxml=result.xml"]
bc0.failedUnstableThresh = 1
bc0.failedFailureThresh = 1


// bc1 = utils.copy(bc0)
// bc1.build_cmds[0] = "conda install -q -y python=3.5"

// Iterate over configurations that define the (distributed) build matrix.
// Spawn a host of the given nodetype for each combination and run in parallel.
utils.run([bc0])