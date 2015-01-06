![django-scarface](logo_transparent.png)

# Welcome to django-scarface

Send push notifications to mobile devices using Amazon SNS.

## Getting Started

### Setup
You can install Scarface directly from pypi using pip::

	$ pip install django-scarface


Edit your settings.py file::

	INSTALLED_APPS = (
		...
		"scarface",
	)


Native Django migrations are supported on Django 1.7 and beyond. The app will automatically
fall back to South on older versions, however you will also need the following setting::

	SOUTH_MIGRATION_MODULES = {"scarface": "scarface.migrations"}

Add your AWS credentials andthe required settings for Apple Push Notifications and/or Google Cloud Messaging as documented in the [Settings Chapter](#settings).


## Settings
The following settings are required:

The credentials of your AWS user. We expect the user to have all the priviliges to create Applications, Endpoints and Topics

    AWS_ACCESS_KEY = "<YOUR_AWS_ACCESS_KEY>"
    AWS_SECRET_ACCESS_KEY = "<YOUR_AWS_SECRET_ACCESS_KEY>"

The mode for Apple Push Notifications. Either "APNS" for production or "APNS_SANDBOX" for the sandbox environment.

    SCARFACE_APNS_MODE = u"APNS_SANDBOX"

The name of the application that will be created. This name is later postfixed with the platform, for example the Application name will be 'Scarface_Test_gcm' or 'Scarface_Test_apns'

    SCARFACE_SNS_APP_PREFIX = u"Scarface_Test"

Your Google Cloud Messaging Key. It is expected to be a Server-Key

    SCARFACE_GCM_API_KEY = "<YOUR-GCM-API-KEY>"

The APNS certificate and private key as a string. you can create this settings by using the "manage.py extract_keys" command and a P12 file.

    SCARFACE_APNS_CERTIFICATE = "<YOUR-APNS-CERTIFICATE-KEY>"
    SCARFACE_APNS_PRIVATE_KEY = "<YOUR-APNS-PRIVATE-KEY>"


## Management Commands
### extract_keys
You can extract the SCARFACE_APNS_CERTIFICATE and SCARFACE_APNS_PRIVATE_KEY settings from a .p12 file exported from Keychain Access. The usage is as simple as the following example:

    python manage.py extract_keys --file=Certificate.p12 --password=<MYPASSWORD>

The output can be copied and pasted into your settings file.

## Usage
### Devices Registration
### Send Push Notifications



Now have fun using this library and [push it to the limit](https://www.youtube.com/watch?v=9D-QD_HIfjA).

![the movie](scarface-movie.png)