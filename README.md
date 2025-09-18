
## Install and remove NodeJS on Ubuntu server

### **Install NodeJS**

It is recommanded to install NodeJS using Node Version Manager(NVM)

``` console
sudo apt update && apt upgrade -y
```

``` console
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

After that, reload the shell so **nvm** is available:

``` console
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
```
Then verify the version
``` console
nvm --version
```

Now install node.js
``` console
nvm install 22
```

Check the version
``` console
node -v
npm -v
```


### **Remove NodeJS**

It is better to remove NodeJS and its modules manually because installation leaves a lot of files, links and modules behind and later this creates problems when we reconfigure another version of NodeJS and its modules.

To start deletion execute the following commands
``` console
sudo apt-get remove node
sudo apt-get remove nodejs
sudo apt-get remove npm
```

To remove the files, run the following commands:

``` console
sudo rm -rf /usr/local/bin/npm 
sudo rm -rf /usr/local/share/man/man1/node* 
sudo rm -rf /usr/local/lib/dtrace/node.d
rm -rf ~/.npm
rm -rf ~/.node-gyp
sudo rm -rf /opt/local/bin/node
sudo rm -rf /opt/local/include/node
sudo rm -rf /opt/local/lib/node_modules
sudo rm -rf /usr/local/lib/node*
sudo rm -rf /usr/local/include/node*
sudo rm -rf /usr/local/bin/node*
sudo rm -rf ~/.npm-global
```

Then execute
``` console
sudo apt-get update
```

Check for any .npm or .node folder in your home folder and delete those.

``` console
which node
which nodejs
which npm
```
