# The `config` directory

Files in this directory will be installed into a user's `/etc` diretory __AFTER__ any packages necessary are installed.

Any pre-existing folders will be used, while pre-existing files that would normally be overwritten will be handled in one of 2 ways, depending on a users configuration:

 * the file that would normally be overwritten will simply be given a `mod_bak` suffix, after the file extension.
 * the file will be copied, unmodified, into another directory elsewhere, under an identical file path
 
This is to allow de-configuration when a mod is uninstalled.