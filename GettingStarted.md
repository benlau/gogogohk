**Table of Content**


---

# Repository #

Repository is on [github](http://github.com/gogogo), perform the following to get a copy.
```
git clone git://github.com/gogogo/building.git  # development utilities codebase
git clone git://github.com/gogogo/gogogo-hk.git # project codebase
```

For developers who contribute to the project, perform the following instead.
```
git clone git@github.com:gogogo/building.git  # development utilities codebase
git clone git@github.com:gogogo/gogogo-hk.git # project codebase
```

---

# GAE SDK #

In order to start working, you also need the Google App-Engine SDK. You may obtain a copy from [here](http://code.google.com/appengine/downloads.html).

**Note**
  * You need Python 2.5 to run the SDK
  * Gogogo project is only compatible with GAE SDK 1.2.2+

---

# Development server #

## settings\_private.py ##

settings\_private.py keeps all keys used in the environment. Keys include...
  1. django secret key
  1. google maps api key

Linux user can generate a django secret key by using _pwgen_. Following snippet create the settings\_private.py for local development server.
```
cd gogogo-hk
cat << EOF > settings_private.py
KEY="`pwgen 40 `"
GOOGLE_MAPS_KEY="ABQIAAAAzr2EBOXUKnm_jVnk0OJI7xSosDVG8KKPE1-m51RBrvYughuyMxQ-i1QfUnH94QxWIa6N4U6MouMmBA"
EOF
```

**Note**
  * Google Maps API key is domain dependent. You may need to obtain your key for domain that is not localhost:8000
  * For Windows fans, please seek help from others to obtain an unique django secret key. Otherwise, you may use this shared django secret key "sohkoihiijudiecaivaichaipeigheighaumaiyo"

## Cloning GAE SDK ##

For Windows fans, you are recommended to copy the folder of _C:\Program Files\Google\google\_appengine_ into _gogogo-hk\common\_

For Linux fans, you are recommended to create a symbolic link to the folder _gogogo-hk/common/_ by
```
ln -s {path_to_app_engine} {path_to_gogogo_hk}/common/.google_appengine
```

**Note**
  * For Linux fans, prevent copying the sdk directly into _/gogogo-hk/common/_. Otherwise, python ImportError will be resulted.

## Using Media Generator ##

All media files should be stored under generated\_media/_, but don't put anything into__generated\_media_. Instead, you should use the generator by performing
```
./manage.py generatemedia
```

## Kicking off the Server ##

Perform the following under _gogogo-hk/_ folder and you will get Gogogo running on http://localhost:8000.
```
./manage.py runserver
```

Alternatively, Perform the following under _gogogo-hk/_ folder and you can preserve data:
```
{path_to_gae_sdk}/dev_appserver.py --datastore_path ../gogogo.bin .
```

## Importing Data ##
  * Get a copy of test data by [here](http://code.google.com/p/gogogohk/downloads/list), extract it into _building/data_
  * Start your development sever and perform the following
```
# You SHOULD have GAE SDK in your $PATH environment variable
# PATH=$PATH:{path_to_gae_sdk} python bulkloader.py is a good shortcut to do so

cd building
./bulkloader.py -d all # Upload all testing data to dev-server

#./bulkloader.py --help for options
# You may alternatively run
./bulkloader.py -d agency # uploading agency data to dev-server
./bulkloader.py -d stop   # uploading stop data to dev-server
```

**Note**
  * You may read [DataImportGuide](DataImportGuide.md) for data import format
  * You may also use bulkloader to deploy data onto deployment server by issuing
```
# You SHOULD have GAE SDK in your $path environment variable
./bulkloader.py --url http://test.gogogo.hk -d all
```

## Default Admin in Dev server ##
AppEngine dev server, by default, allows any login name to access the system, and it will create a record for that user. Visit the django-admin interface (/admin) and you may set the "Staff" and "Superuser" status for anyone.

However, the default setting in settings.py does not allow such to do so. If you want to re-enable the above default behavior, comment out the following line in settings.py and restart the dev server.
```
AUTH_ADMIN_USER_AS_SUPERUSER = False
```

For deployment, re-enable the setting as it disallows Google Accounts being marked as  superuser and staff. See [issue 51](http://code.google.com/p/gogogohk/issues/detail?id=51&can=1&q=owner%3Amr.kschan#c3) for details.

## Clustering ##

Stops are clustered into areas before performing any query. You have to cluster your own dataset if you want to build an environment. To do so, you need [gaescripts](http://github.com/benlau/gaescripts). Get a copy of [gaescripts](http://github.com/benlau/gaescripts) and keep it on the same directory as building/ and gogogo-hk/ is resided.

  * Keep your dev-server running
  * Do the following.

```
cd building
../gaescripts/gae-remote-run.py -d ../gogogo-hk clusterer
```

---

# FAQ #

Q.
raise yaml\_errors.EventError(e, event\_object) google.appengine.api.yaml\_errors.EventError: Unable to assign value '[.md](.md)' to attribute 'skip\_files': Value '[.md](.md)' does not compile: unexpected end of regular expression

A.
Make sure you have GAE SDK 1.2.2+