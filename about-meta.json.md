# meta.json
## Overview
`meta.json` is a metadata file, similar to the `control` file found in Debian packages, or the `*.spec` file for RPM packages: it provides information as to a mod's name, a short and long description, version code, and a dependency list (known as a package list).

## File View
> {
> 	"mod_name": "Example Mod Name",
> 	"short_desc": "This is an example mod",
>	  "long_desc": "This is an example mod, designed to help developers see what a Drauger OS mod would be formatted like.",
> 	"mod_version": {
> 		"version_code": "0.0.1",
> 		"version_status": "experimental",
> 		"code_name": null
> 		},
> 	"package_list": [
> 		"package1",
> 		"package2",
> 		"package3"]
> }