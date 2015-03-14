**Table of Content**


# GAEScripts #

Gaescripts - A collection of scripts for GAE application maintenance
http://github.com/benlau/gaescripts/tree/master

It is a project designed for Gogogo to manage different tasks including backup and restore.

Repository - git clone git://github.com/benlau/gaescripts.git

## Backup ##

```
Usage: gae-backup.py <application root>

Options:
  -d, --debug          
  -u URL, --url=URL    
  -e EMAIL, --email=EMAIL
  -o OUTPUT, --output=OUTPUT  The output path of backup.
  -h, --help                  Show this help message.
```

### Backup from Development Server ###

```
{path_to_gaescripts}/gae-backup.py -d {path_to_gogogo_src}
{path_to_gaescripts}/gae-backup.py -d {path_to_gogogo_src} -o {output} # save backup files in output directory
```

### Backup from Deployment Server ###
```
{path_to_gaescripts}/gae-backup.py -e {email_address} {path_to_gogogo_src}
```

## Restore ##

### Restore to Development Server ###

```
{path_to_gaescripts}/gae-restore.py -d {path_to_gogogo_src} {backup_path} # Restore from folder
{path_to_gaescripts}/gae-restore.py -d {path_to_gogogo_src} backup/gogogo_agency.json # Restore from individual file
{path_to_gaescripts}/gae-restore.py -d {path_to_gogogo_src} {backup_path} backup/gogogo_agency.json backup/gogogo_stop.json  # Restore from folder and individual files
```