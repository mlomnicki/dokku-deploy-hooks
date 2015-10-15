Deploy Hooks plugin for Dokku
=============================

The plugin adds support for pre- and post-deploy hooks to dokku.

Hooks can be used to run tasks upon deployment, such as
database migrations, syncing assets or generating a sitemap.


Installation
============

    cd /var/lib/dokku/plugins
    git clone https://github.com/mlomnicki dokku-deploy-hooks deploy-hooks

Usage
=====

In your application repository create a file named `deploy/pre-deploy` or `deploy/post-deploy`.
For example

    #!/bin/bash

    rake db:migrate
    rake airbrake:deploy TO=$RAILS_ENV
    curl http://example.com/check-deploy

Note that the file is a regular script. You can use any language to write it!
Just remember to set the correct shebang line (like #!/bin/bash if you want to execute bash code).

Next make it executable

    chmod +x deploy/pre-deploy

From now on your script will be executed every time you deploy the app.

    git push dokku master

    -----> Cleaning up ...
    -----> Building

    -----> Running pre-deploy hooks
    -----> deploy/pre-deploy found. Running it ...

MIT License
===========

Copyright (C) 2015 Michal Lomnicki

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
