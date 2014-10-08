# ozp-webtop

[![Build Status](https://travis-ci.org/ozone-development/ozp-webtop.svg?branch=master)](https://travis-ci.org/ozone-development/ozp-webtop)

Next Gen OZONE UI

## Prerequisites
Install Node.js and npm. Head over to [the Node.js website](http://nodejs.org/) 
if you need to do that.
Next, install [Grunt](http://gruntjs.com/) and [Bower](http://bower.io/) with 
the command below.

    (sudo) npm install -g bower grunt-cli

## Getting Started
First clone the repo. Then install development dependencies with npm. Install 
frontend app dependencies with Bower:

    cd ozp-webtop
    npm install && bower install
    
### Grunt Tasks
Development tasks are run with Grunt. 

 - `grunt serve` 
     * brings up a live preview of the webtop on http://localhost:9000
     * live preview of the docs on http://localhost:9010
 - `grunt build` - executes unit tests
 - `grunt gh-pages` - run after a `grunt build` to publish the build files to [gh-pages](http://ozone-development.github.io/ozp-webtop/)
 
Run `grunt -h` for a full list of Grunt tasks.

## Development Notes

### Use of ng-boilerplate
This app was created from [ng-boilerplate](https://github.com/ngbp/ngbp).
ng-boilerplate uses an opinionated build system that separates files by 
feature/component instead of file type. See the ng-boilerplate repo for detailed 
documentation.

### Directory Structure
The directory structure is a result of ng-boilerplate, but is outlined below: 

```
bin                     # output generated by 'grunt compile'. Production-ready
                        # app (compressed, minified, etc)
build                   # output generated by 'grunt build'. Development-ready
                        # app (not compressed or minified)
demoApps                # examples or placeholders for actual OZP widgets/apps
    bouncingBalls       # the bouncing balls demo (an IWC-enabled application)
    simpleApps          # trivial 'application' examples
karma                   # files specific to karma, a JavaScript test runner
    karma-unit.tpl.js   # karma config file, processed as a Grunt template to 
                        # avoid manual entry of file names
node_modules            # location of installed Node.js dependencies
src                     # our application's source (and a few other things)
    app                 # application-specific JS and HTML templates
        appToolbar      # the toolbar at the bottom where apps can be pinned
        dashboardToolbar# the toolbar at the top for dashboard selection, etc
        dashboardView   # the main part of the page where widgets are displayed
        general         # services, directives, and other things not specific to 
                        # a single feature/component
    assets              # images and anything else that should be copied verbatim
                        # into the build_dir and compile_dir directories
    common              # components that are broadly reusable and not specific
                        # to the application itself
    less                # CSS and LESS files for this application
    index.html          # the index page for our Single Page App (SPA). It's 
                        # processed as a Grunt template so we don't need to 
                        # manually include any CSS or JS files
vendor                  # third-party resources installed by Bower                      
.bowerrc                # configures bower to store components in a 'vendor' 
                        # directory (instead of bower_components)
.travis.yml             # Travis-CI configuration
bower.json              # Bower configuration
build.config.js         # defines the files (or file patterns) used to determine
                        # the files used for various parts of our application's 
                        # build process. Note that any vendor files must be 
                        # explicitly added here (not just to Bower)
Gruntfile.js            # Gruntfile - defines the build process. Identical to 
                        # Gruntfile found in ng-boilerplate, except for changes
                        # noted at the top of the file. Refer to comments for 
                        # the 'build' and 'compile' tasks in the Gruntfile for 
                        # details on the build process. Most important grunt 
                        # tasks are: 'build', 'compile', and 'serve'
module.prefix           # the application script is wrapped in module.prefix and
                        # module.suffix to place the app inside of a self-
                        # executing anonymous function to prevent clashes with 
                        # other libraries
module.suffix           # see above
package.json            # metadata about our app, used by NPM and the build 
                        # script. NPM dependencies are listed here
.gitignore              # files and patterns to ignore for version control
```

## Conventions, Style, etc.
* All HTML templates named *.tpl.html
* All JavaScript test files named *.spec.js
* If you modify the Gruntfile, make sure the modification is noted in comments at 
 the top of the file. This will ensure the original ng-boilerplate docs remain
 as useful as possible
* JavaScript style - use Google's conventions (2 space indentation)
* HTML style - use 2 space indentation 
* Try to keep lines to 80 characters whenever possible

### Responsive Design
Currently, Webtop is semi-responsive, supporting devices >= 768px ('small' devices,
as defined by Bootstrap). 

## Production Deployment
To run the production version of Webtop (files minified, concatenated, etc):

1. Follow the steps in the Prerequisites and Getting Started sections above
2. Run ```grunt```. This will create a ```bin/``` directory - statically host
```bin/``` and you're good to go!
3. For testing the production version, run ```grunt run```


## Copyrights
> Software (c) 2014 [Department of Defense](http://defense.gov/ "DoD")

> The United States Government has unlimited rights in this software.  
 
The OZONE Platform Webtop is released to the public as Open Source Software, because it's the Right Thing To Do. Also, it was required by [Section 924 of the 2012 National Defense Authorization Act](http://www.gpo.gov/fdsys/pkg/PLAW-112publ81/pdf/PLAW-112publ81.pdf "NDAA FY12").

Released under the [Apache License, Version 2](http://www.apache.org/licenses/LICENSE-2.0.html "Apache License v2").
