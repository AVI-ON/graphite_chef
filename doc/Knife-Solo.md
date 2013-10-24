## Knife Solo
Knife Solo is the tool we use to interact with Chef Solo.
This gives us easy access to Chef commands and automates the setup
of the chef "kitchen".

###Init command
The init command simply takes a name of the directory to store the kitchen structure. Use “.” to initialize the current directory.

````bundle exec knife solo init <myKitchenDirectory>````

## Node Setup and configuration

On the roles folder we configure each of the different server roles we will have.
Each server node is then represented by an entry on the nodes folder.
File name must be the host name for the particular node.

The node file will include a run list with the list of roles for the server.

## Preparing a node

Once the nodes have been configured we first need to prepare the environment
running:

````bundle exec knife solo prepare <user>@<hostname>````

This will copy chef to the new node. Hostname can be a host configured
in .ssh/config

````bundle exec knife solo cook <user>@<hostname>````

Will run the recipes for the server and complete the setup of the instance.



http://matschaffer.github.io/knife-solo/