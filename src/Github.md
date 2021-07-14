{% include _includes/nav.md %}

## Github

<!-- ## CI (Github Actions)
### Building
We use Github Actions to build all our assets then copy the files over to the server once they have been built.

### SSH
In order for a Github action to SSH into a given server, you will need to create a new SSH key. 
1. SSH into the server and generate the new SSH key using `ssh-keygen -m PEM -t rsa -b 4096`.
2. Name the file action_rsa
3. Don't generate a passphrase
4. Copy the Public SSH key using `cat ~/.ssh/actions_rsa.pub`
5. Add a new SSH key to the server you are targeting in Forge. For example [PAPER-TIGER-STAGING](https://forge.laravel.com/servers/209262#/keys)
6. Next, copy the private SSH key `cat ~/.ssh/actions_rsa`
7. In the repo for the project, go to Settings>Secrets (https://github.com/PaperTiger/[REPO]/settings/secrets) -->