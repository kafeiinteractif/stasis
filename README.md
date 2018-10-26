# stasis

Single-site Docker environment for Drupal local site development and
migrations, for sites which feature a docroot.


## Before you begin

Open a terminal window and run the following:

    docker-compose up

You can control-C to close this window when you are done using the servers.
Meanwhile, you can watch these logs to see if anything weird is happening in
your site.

    docker-compose down

This will stop the process from a different terminal window.

Now that you have docker-compose up running, you are ready to do setup.



## Setup:

*Make sure that repo/docroot exists in this folder, containing your site's code first!*

    ./deploy init        # copies the site's default.settings.php and default.services.yml
			 # to settings/settings.php and settings/services.yml
			 # so you can edit these if you need. The DB is set at
			 # the bottom if you add d7 or d8 as parameters (see
			 # below).  Docker will mount settings as
			 # docroot/sites/default.

    ./deploy init d7     # Will inject the DB values as well
    ./deploy init d8     # Will inject the DB values as well

    ./deploy si          # run the site installer
    ./deploy db          # import the sql/drupal.sql.gz



## Get a terminal and find public IP

Drush and drupal console are already installed.

    ./deploy


## Migrations.

A secondary database called drupal_legacy is already configured and
works the same as the regular db import command:

    ./deploy db_legacy   # import the sql/drupal_legacy.sql.gz DB

## Delete DB

It will destroy the database container, so all DBs will be removed in one go.
Server will restart when it is killed, so reloading will cause site installer
to begin.

    ./deploy xx       # delete the DB so you can run a fresh db import later
