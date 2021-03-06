heroku-mono-build
=================

Builds Mono and related packages, assembles them for deployment, and uploads them to S3 for use by [heroku-buildpack-mono](https://github.com/brandur/heroku-buildpack-mono).

Clone the build repository:

    git clone https://github.com/brandur/heroku-mono-build.git
    cd heroku-mono-build

Create a Heroku app and store your secrets there:

    heroku create heroku-mono-build --buildpack https://github.com/kennethreitz/buildpack-null.git
    heroku config:add AWS_ID="..." AWS_SECRET="..." S3_BUCKET="heroku-buildpack-mono"
    heroku config:add MONO_VERSION="2.11.1"

Now shell into your new app and kick off a build:

    heroku run bash
    bin/build-mono && bin/build-xsp
