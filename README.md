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


##	How?
###	Config files are stored orderly in a directory.

Using `git`, one can version and change them.
- Using `rsync` &  `git` one can backup them into a seperate branch and thus make it easy to backroll changes.
- Using `ssh` and the `authorized keys` feature, access control is also versioned.
  - No need to fiddle with `secrets` or `vaults`.


###	Structured approach to configuration.

All configuration files are where they are expected.
- No need to have some configuration file parser, just simple files and changes.

Configuration is as portable as can be.
- All config files are where they are expected.

Backups are a breeze.
- Just make a pull of the `git` and shove it wherever you feel it's most secure.

