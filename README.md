Works4me: CLI-configurable Vagrant-based test VM
================================================

"Easily spin up a disposable VM with selectable guest OS, Memory, Java version, etc."

"As a developer, I want a VM I can easily configure, so I can quickly test customer configurations"

Depends on Vagrant: https://www.vagrantup.com/downloads.html 

Once Vagrant is installed, it can be run as usual:

Create & run a new VM per Vagrantfile defaults:
    $ vagrant up

Log in to new Vagrant VM via SSH:
    $ vagrant ssh

Observe VM OS name, etc.
    $ uname -a

Observe provisioned Java version:
    $ java -version

Now, teardown *that* VM, so we can create a new one, with different attributes:
    $ vagrant destroy

    $ vagrant --memory=2048 --os=precise32 --java=openjdk-6-jre up

Log in to new Vagrant VM and look around, as above:
    $ vagrant ssh
    $ uname -a
    $ java -version

Note that since we are using Vagrant, instead of destroying our VM,
we could have simply used "vagrant halt" to halt it,
and then "vagrant up" later to resume using it.
However, if we want to change the VM attributes,
then we need to re-generate it, and this (to the best of my current knowledge)
requires that we use "vagrant destroy" to remove the configured VM.

TODO:
1. Clean up the README.md file! :)
1. Check if "vagrant destroy" is really necessary to reconfigure VM?
1. Improve help info.
1. Improve option error handling.
1. Refactor settings code to improve maintainability.
1. Tests

-- m0j0hn, 2016-02-19
