# sconfm
Simple CONFiguration Manager 
- A brutally simple way to manage system(s) configuration(s)!

---

##	Why?

###	I really *hate* YAML and other preprocessing languages and the complexity of a lot of tools like Ansible that use them.

It's not that I can't use them, I frankly am forced to. But I find them quite unelegant and not cool in terms of actually being able to look at config file differences.
- And if I have to version the actual config files to catch errors, I might just directly version the config files properly.


###	A *"stupid edge"* approach.

We don't want to install *yet another tool* on a specific server, but be able to just deploy/restore a specific config.
- The config managment and -versioning is done with `git` and/or the IDE/editor of choice for the admins.
- No need to setup *yet another server* just to manage the *"slaves"*.
  - Works with anything one can mount and run git through!


### A more *flexible and portable* approach!

Tools like Ansible, Saltstack, Guix, etc. are all fine and useful -  no question about that - but they do require supporting the target systems' OS.
- Usually said Configuration Managment solutions require the ability to if not *install* their own *"agent"*, at least run / deploy one as a persistent executeable, which necessitates the ability to install, add and run arbitrary code.
- They also tend to require if not `root`, at least `sudo` privilegues or at the absolute minimum a local shell. 
  - Something that may *purposefully* be absent in many cases (i.e. shared Webservers & Webhosting/Application Hosting offers).


##	How?
###	Config files are stored orderly in a directory.

Using `git`, one can version and change them.
- Using `rsync` &  `git` one can backup them into a seperate branch and thus make it easy to backroll changes.
- Using `ssh` and the `authorized keys` feature, access control is also versioned.
  - No need to fiddle with `secrets` or `vaults`.

Simple hierachy of files:
- [`configs`](configs) - configurations
  - [`homes`](configs/homes) - `$HOME` directories
    - `$USERs` - user's homes to be configured.
  - [`hosts`](configs/hosts)
    - `$FQDNs` - the hosts in question
      - *configuration files*
    - [`hosts.tsv`](configs/hosts/hosts.tsv) - lists of the hosts.
  - [`users`](configs/users) - users to be configured
    - [`users.tsv`](configs/users/users.tsv) - the users to be configured.
- [`scripts`](scripts) - The scripts to acrually manage (backup & deploy) said configs from *any* machine.
  - [bash](scripts/bash) - `bash` scripts
    - *scripts*


###	Structured approach to configuration.

All configuration files are where they are expected.
- No need to have some configuration file parser, just simple files and changes.

Configuration is as portable as can be.
- All config files are where they are expected.

Backups are a breeze.
- Just make a pull of the `git` and shove it wherever you feel it's most secure.


