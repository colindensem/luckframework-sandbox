# Crystal & Lucky Framework using VS Code remote containers

I have many projects/experiments, I am moving towards having docker local development for each. Next step is in the cloud from an ARM laptop.

Firstly, a misnomer, remote, isn't remote in the sense of a remote cloud server. You can do that with remote ssh connections, however not presently with docker-compose and one click...

To this end I've turned my focus to visual studio code, the remote docker container extension.

For this to work, you'll need:

* A local copy of VSCode - I'm using insiders.
* Some vscode extensions
  * ms-vscode-remote.remote-containers
  * ms-azuretools.vscode-docker
* A host that has docker setup for your user. `docker ps` works etc.

## Getting started

Open VS Code and install the extensions listed above.

You now have access to the remote container operations. Press `F1`, enter `Remote-Containers` to see the list of possible commands. Read up on each, or...

Lets do this:

* Press `F1` again, and enter `Clone Repository in Container Volume`.
* Select Github, or enter your repo's URL, or this one.
* Wait a few moments for VS Code to do the setup, watch the log if you like.

Alternative, is to clone this repo, and then open in vscode with the extensions installed. You'll be prompted to reopen in a container.

Either way, once the container has started, you should be able to open an integrated terminal within VS Code and do the following:

```bash
crystal -v

lucky -v

overmind -v

crystal hello-world.cr
```

Make any changes you wish, and commit, and push, from your container. `gnupg` is installed for verified commits from within VS Code.

## Checking the project

Close VS Code and reopen it. It will be a blank window, we want to reconnect to the now stopped remote container.

From the File menu > Open Recent > Select your project name in a unique docker volume [Dev Container]

Explore the extension, and docker/containers generally. See bonus section below for some incredibly handy tools for managing docker.

A quick note on extensions, the `devcontainer.json` includes the two key extensions to write crystal, & edit the docker file. In addition I've added a resource monitor as it's interesting to see while compiling. You can add more here, or add your own.

It would be wise; certainly in a multi-dev environment, to have a core set of extensions, then leave each dev to use there own flavour of theme, bracket rainbows etc.

You can easily install an extension into the container using the extensions tool, once connected to your container.

## Next steps

The repo has support to start a fresh lucky project. Just use `lucky init` and move the files accordingly to this context. Not forgetting to remove the `hello-world.cr`

Open VS Code, your recent project, then the integrated terminal. Run `script/setup` followed by `lucky dev`. Now open your browser to `localhost:5000`

## Closing thoughts

This simple example is only the start. I'll explore it with my lucky/crystal projects and update this as I learn/discover what works or doesn't.

## Troubleshooting

### It's not working

Welcome to docker :) things change. I've had it work one day, not the next. If it's really not working, clear down containers, volumes and optional images, start a fresh. Once you've tried to debug it using the given log options.

### GPG

If you want verified commits there are a few hoops to jump through, but it's pretty much sorted.

* You need GPG commits working locally first.
* You need your local `.gitconfig` to use a `gpg2` on your resolved path.  Assuming your local and remote host os are different, you don't want `c:/foo` and `/usr/local/bin`.
* Read the [Github Issue][3] that covers the test for gpg.
* Try a commit...

## Bonus tools for your remote host

Additional tools to make your remote, or local docker life easier.

* [ctop][1]
* [lazydocker][2]

[1]:https://github.com/bcicen/ctop
[2]:https://github.com/jesseduffield/lazydocker#installation
[3]:https://github.com/microsoft/vscode-remote-release/issues/3053
[4]:https://digitalocean.com
[5]:https://m.do.co/c/8ff05d02841e
