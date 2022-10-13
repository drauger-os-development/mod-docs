# meta.json
## Overview
`meta.json` is a metadata file, similar to the `control` file found in Debian packages, or the `*.spec` file for RPM packages: it provides information as to a mod's name, a short and long description, version code, and a dependency list (known as a package list).

## File View
```
{
	"mod_name": "Example Mod Name",
	"short_desc": "This is an example mod",
	"long_desc": "This is an example mod, designed to help developers see what a Drauger OS mod would be formatted like.",
	"mod_version": {
		"version_code": "0.0.1",
		"branch": "alpha",
		"code_name": null
		},
	"package_lists": {
		"dpkg": [
			"deb-package1",
			"deb-package2",
			"deb-package3"],
		"dnf": [
			"rpm-package1",
			"rpm-package2"],
		"zypper": [
			"slackware-package"],
		"pacman": [
			"arch-package1",
			"arch-package2",
			"arch-package3",
			"arch-package4",
			"arch-package5"],
		"eopkg": [],
		"emerge": ["gentoo-package"]
		}
}
```

## Element descriptions

Unless otherwise stated, __all elements are mandatory__.
### `mod_name`
The name of your mod.

### `short_desc`
A short description of your mod. Try to keep this below about 200 characters. This is the first description of your mod users will see usually.

### `long_desc`
This is effectively the same as `short_desc`, except without the character limit. This is where users will likely go first for more information on what your mod is and does.

### `mod_version`
This element contains various version information. Some of which is optional.

#### `version_code`
`version_code` contains a simple version code for your mod. This may allow for pushing updates to mods later on.

Version codes should ALWAYS follow the following format:
<pre>
major version . minor version . patch version
</pre>
If you only wish to use 2 digits in your version code, leave the last number (patch version) set to zero (0). If you only wish to use 1 digit, use the first one (the major version), and set the remaining two to zero (0).

Version codes may be any, arbitrary, positive number. Examples:

 * 0.0.1
 * 1.5.2
 * 20.55.101
 * 0.400.20
 * 23.0.0
 * 69.420.0
 * 0.38.0
 
Due to the way version codes are parsed and understood, you may think of it like working like a real number:

<pre>
1.0.0 > 0.1.0 > 0.0.1
2.0.0 > 1.0.0
2.4.5 > 1.36.2 > 1.35.45 > 1.35.40
</pre>

#### `branch`
This __optional__ element is useful if you want to have users to get updates on different branches. Usually, these should be:
 * `stable`, `production`, `master`, or `main` for your default branch
 * `beta` or `testing` for your beta testing branch
 * `alpha` or `experimental` for your alpha testing branch
 * `dev` , `develop`, or `development` for your development branch
 
If a user has configured their system to only take updates from a specific branch, they will only receive an update you publish if it is published on the branch they are tracking.

If your package does not use branches, you may either:

set this element to `null` (prefered) or `"None"`

 OR
 
leave this element out of your `meta.json` file entirely.

If you do not use branches and a user configures their system to track a specific branch, their setting will be ignored and they will continue to receive updates.

If a user sets an invalid branch name to be tracked, their setting will be ignored and their system will default to the `stable` branch.

If a developer sets an invalid branch name for a mod package version, it will be ignored and the package will be assumed to belong to the `development` branch.

#### `code_name`
`code_name` is an __optional__ element that can add a bit of personality and life to a mod. Any `code_name` should be shorter than 30 characters, but may be whatever the developer chooses, and change however often the developer chooses.

Any `code_name` will always be shown next to a given `version_code`.

### `package_lists`
This is an __optional__ dictionary of lists of packages that will be installed __BEFORE__ files in the `config` directory are handled.

Packages listed under here should be listed under the package manager the name is known under. Some package managers have aliases:
 * `dpkg` may also be referred to with `apt` or `aptitude`.
 * `dnf` may be referred to with `rpm`
 * `zypper` is aliased to `yast`
 * `eopkg` is aliased to `sol`
 
Client-side interfaces will do one of two things:
 * Be designed from the ground up for a specific package manager, and thus ignore everything else
 * Be designed to be cross-platform, and thus be capable of figuring out which is in use and inferring from there.
 
If your mod does not have a package list for a specific package manager, it will not be installed.

# Curated Tour of how Drauger OS Mods work
The next step is learning about the `config` directory: [click here to learn about the `config` directory](https://github.com/drauger-os-development/mod-docs/blob/master/config/config.md/blob/master/about-meta.json.md)!