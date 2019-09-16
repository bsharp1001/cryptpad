[![An XWiki Labs Project](https://raw.githubusercontent.com/xwiki-labs/xwiki-labs-logo/master/projects/xwikilabs/xlabs-project.png "XWiki labs")](https://labs.xwiki.com/xwiki/bin/view/Main/WebHome) : **with a # touch**

![CryptPad screenshot](https://github.com/xwiki-labs/cryptpad/raw/master/screenshot.png "Pads are an easy way to collaborate... and more secure with p2p decentralized storage")

CryptPad-ipfs \(CryptPad#\) is the **Zero Knowledge** realtime collaborative editor, with a simple IPFS storage mechanism made by bsharp# to make the storage more secure and with more hashing in the process.

Encryption carried out in your web browser from the normal cryptpads`s mechanisms added to it IPFS encryption mechanism protects the data from the server, the cloud and the NSA. It relies on the [ChainPad] realtime engine.

<!--If you'd like to know more, please read [the Whitepaper]().-->

# Installation

There are 2 ways of installation described here:

1. [Install from the original CryptPad repo then add the storage mechanism](https://github.com/bsharp1001/cryptpad/#user-content-1-installation-from-original-repo)

2. [Install this fork directly](https://github.com/bsharp1001/cryptpad/#user-content-2-installation-from-this-fork)

## 1. Installation from the original Repo:

follows the same steps in the original Guide [here](https://github.com/xwiki-labs/cryptpad/wiki/Installation-guide)
or to sum it up, here are the steps with commands: 

### 1. Pre-requisites

   - git
   - nodejs \([NVM](https://github.com/creationix/nvm) Usage recommended for managing different versions of node\)
        -To install the default current version of node:

            sudo apt-get install curl
            curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
            sudo apt-get install nodejs

   - npm: `sudo apt-get install npm`
   - bower: `npm install -g bower`

### 2. Cloning

   - Clone the repository: 

        git clone https://github.com/xwiki-labs/cryptpad.git

### 3. Dependencies

    cd path/to/cryptpad
    npm install
    bower install
`npm install ipfs` or `npm i ipfs`

### 4. Adjust configuration

   `cd /path/to/cryptpad/config` or if you are already in the installation directory `cd config`
   `cp config.example.js config.js`

### 5. Applying the storage:

- Copy the source code from this link: https://github.com/bsharp1001/cryptpad/blob/master/storage/file.js and save it in a file in `path/to/cryptpad/storage/yourcustomfilename.js`

- Open the file `config.js` located in the folder `config`, find the line `storage: './storage/file',` at the end of the file and change `file` with the custom name of your file. That's it! now:

### 6. Run CryptPad-ipfs

    node server

And we're done! your CryptPad should now be available at `localhost:3000`

### 7. Upgrade 

As in the Original wiki installation Guide [here](https://github.com/xwiki-labs/cryptpad/wiki/Installation-guide#user-content-upgrading-cryptpad). Here the summed-up steps:

        cd path/to/cryptpad
        git pull
        npm update
        bower update

## 2. Installation from this fork: 

Follow the instructions below or for summing-up just go to [the ready-made Command Board](https://github.com/bsharp1001/cryptpad/#user-content-command-board)

### Instructions

Installation of this fork pretty much follows the same steps in the original Guide \(**installation steps only, not Upgrading steps.**\) [here](https://github.com/xwiki-labs/cryptpad/wiki/Installation-guide) **EXCEPT for 2 major different steps:**

1. Clone the repository from this fork not from the original repo:

        git clone https://github.com/bsharp1001/cryptpad.git

2. install jsipfs library **in CryptPad installation directory** \(assuming you have npm installed\):
   
        cd path/to/cryptpad
        npm i ipfs

### Command Board

#### 1. Pre-requisites

   - git
   - nodejs \([NVM](https://github.com/creationix/nvm) Usage recommended for managing different versions of node\)
        -To install the default current version of node:

            sudo apt-get install curl
            curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
            sudo apt-get install nodejs

   - npm: `sudo apt-get install npm`
   - bower: `npm install -g bower`

#### 2. Cloning

   - Clone the repository: 

        git clone https://github.com/bsharp1001/cryptpad.git

#### 3. Dependencies

    cd path/to/cryptpad
    npm install
    bower install
`npm install ipfs` or `npm i ipfs`

#### 4. Adjust configuration

   `cd /path/to/cryptpad/config` or if you are already in the installation directory `cd config`
   `cp config.example.js config.js`

#### 5. Run CryptPad-ipfs

    node server

And we're done! your CryptPad should now be available at `localhost:3000`

#### 6. Upgrade (if and only if installation is done from fork)

As we are using a fork we can't just upgrade from the original repositoiry directly as this will remove the current ipfs implementation so we will [sync our fork](https://help.github.com/en/articles/syncing-a-fork) with the original repo which we will call **upstream** from Now on.

- First, check your original repo with this command `git remote -v` executed inside your repository installation directory i.e:
  
    `cd path/to/cryptpad` then `git remote -v`

  the result will be something like this: 
  
        origin	https://github.com/bsharp1001/cryptpad (fetch)
        origin	https://github.com/bsharp1001/cryptpad (push)

- After checking, add the upstream \(original cryptpad repo\) with this command:

        git remote add upstream https://github.com/xwiki-labs/cryptpad.git

- Then check again that the upstream is successfully added to yoour local installation and that the origin and upstream exist together with the command `git remote -v` and the result will be something like this:
  
        origin	https://github.com/bsharp1001/cryptpad (fetch)
        origin	https://github.com/bsharp1001/cryptpad (push)
        upstream	https://github.com/xwiki-labs/cryptpad (fetch)
        upstream	https://github.com/xwiki-labs/cryptpad (push)

Now every time you want to check for updates you can easily do it with this command:

    git pull upstream master

Or with this method for people who prefer the `fetch` n `merge` method:

1. Fetch the upstream:

        git fetch upstream

2. Checkout the local `master` branch:

        git checkout master

3. Merge the changes from upstream/master into your local master branch which will update your local installation without using the ipfs storage mechanism:

        git merge upstream/master 

## Setup using Docker

As in this Guide :
See [Cryptpad-Docker](docs/cryptpad-docker.md) and the community wiki's [Docker](https://github.com/xwiki-labs/cryptpad/wiki/Docker) page for details on how to get up-and-running with Cryptpad in Docker.

## Setup using Ansible

As in this Guide :
See [Ansible Role for Cryptpad](https://github.com/systemli/ansible-role-cryptpad).

# Security

CryptPad is *private*, not *anonymous*. Privacy protects your data, anonymity protects you.
As such, it is possible for a collaborator on the pad to include some silly/ugly/nasty things
in a CryptPad such as an image which reveals your IP address when your browser automatically
loads it or a script which plays Rick Astleys's greatest hits. It is possible for anyone
who does not have the key to be able to change anything in the pad or add anything, even the
server, however the clients will notice this because the content hashes in CryptPad will fail to
validate.

The server does have a certain power, it can send you evil javascript which does the wrong
thing (leaks the key or the data back to the server or to someone else). This is however an
[active attack] which makes it detectable. The NSA really hates doing these because they might
get caught and laughed at and humiliated in front of the whole world (again). If you're making
the NSA mad enough for them to use an active attack against you, Great Success Highfive, now take
the battery out of your computer before it spawns Agent Smith.

Still there are other low-lives in the world so using CryptPad over HTTPS is probably a good idea.

# From the Original Developers:

## Translations

We'd like to make it easy for more people to use encryption in their routine activities.
As such, we've tried to make language-specific parts of CryptPad translatable. If you're
able to translate CryptPad's interface, and would like to help, please contact us!

You can also see [our translation guide](/customize.dist/translations/README.md).

## Contacting Us

You can reach members of the CryptPad development team on [Twitter](https://twitter.com/cryptpad),
via our [GitHub issue tracker](https://github.com/xwiki-labs/cryptpad/issues/), on our
[Matrix channel](https://riot.im/app/#/room/#cryptpad:matrix.org), or by
[e-mail](mailto:research@xwiki.com).

## Team

CryptPad is actively developed by a team at [XWiki SAS](https://www.xwiki.com), a company that has been building Open-Source software since 2004 with contributors from around the world. Between 2015 and 2019 it was funded by a research grant from the French state through [BPI France](https://www.bpifrance.fr/). It is currently financed by [NLnet PET](https://nlnet.nl/PET/), subscribers of CryptPad.fr and donations to our [Open-Collective campaign](https://opencollective.com/cryptpad).

## Contributing

We love Open Source and we love contribution. Learn more about [contributing](https://github.com/xwiki-labs/cryptpad/wiki/Contributor-overview). 

If you have any questions or comments, or if you're interested in contributing to Cryptpad, come say hi on IRC, `#cryptpad` on Freenode.

# License

![AGPL logo](https://www.gnu.org/graphics/agplv3-155x51.png "GNU Affero General Public License")

This software is and will always be available under the GNU Affero General Public License as
published by the Free Software Foundation, either version 3 of the License, or (at your option)
any later version. If you wish to use this technology in a proprietary product, please contact
sales@xwiki.com.

[ChainPad]: https://github.com/xwiki-contrib/chainpad
[active attack]: https://en.wikipedia.org/wiki/Attack_(computing)#Types_of_attack
