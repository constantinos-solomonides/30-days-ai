## Recap and next steps

* Paused due to real-life issues that have been mostly resolved
* The experiment continues, the pause is a data point
* I have succeeded in creating a sandbox for OpenCode using opencode assistant installed in docker container
* I am shifting to use of google Gemini (Google AI pro) - may also incorporate for writing code in sandbox
* Work from CLI, using commits to a repository as the way to communicate

## Real-life pause as datapoint

* AI assistants are not a stand-in
* When the operator (myself) had issues, the work stopped
* Now that the first sandbox is created and can be adapted, it may be allowed to generate articles

## Shift to opencode

* Interactions were not recorded, as it requires some form of CLI session tracking
* Prompt mds **will be** recorded as they can be added in the repository, along with their evolutions
* The plan is to shift to a CLI-based workflow in general, so the time wasted in the back-and-forth to a window does not exist
* The opencode CLI will be used as a kickstart to shift to other assistants (bootstrapping)
* The sandbox was created in two steps:
    * Ask opencode to create the files for a sandbox
    * Manually create a `Vagrant` configuration and set it up to run the containers
* The double isolation is because docker normally runs as root
* Attempt to use Ollama modles locally with opencode worked eventually but it's not viable

## Google Gemini

* The shift is for three reasons:
    * Morally, OpenAI has gone back on their position for use in warfare
    * To try other models in general
    * Because I was dissatisfied with the effort it took to converge with OpenAI

## Next steps

* Update the README.md of the pytest framework project to use also as a prompt
* Generate plantUML code for diagrams
* Expand sandbox to also have a plantUML container, to allow editing docs as well
* Begin implementation of sandbox and then project
