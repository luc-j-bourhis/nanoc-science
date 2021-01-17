# Introduction

An infrastructure built around nanoc to produce contents on the web with a lot of maths and a heavy academic undertone (citations, etc).

# How to setup the build environment?

Ruby is the main dependency, as nanoc is written in that language. The exact version of ruby guaranteed to work is specified in the Gemfile as well as in a .ruby-version for users of rb-env. Eventually, the whole setup boils down to: `bundler install`. If you don't have the right version of ruby, this will fail and complain. Otherwise, all necessary packages will be installed and setup.

# How to build the site?

1. clone this repository.
2. copy file `nanoc.yaml.in` to `nanoc.yaml` and edit it to add author name (later on, when
pulling a new version, you may want to merge the former into the latter instead)
3. create one directory in the `content` directory for each language in which you plan to write articles. Currently, only English and French are supported, directories `en` and `fr` respectively. Then each article shall live inside its own directory within its language directory: its content shall come from a file `index.md` written in markdown (the Kramdown flavour enhanced with features discussed below). Here is an example of hierarchy:

en/
    all about nothing/
        index.md
    is nothing a thing?/
        index.md

fr/
    les pieds nickelés/
        index.md

This will results in 3 articles titled "all about nothing", "is nothing a thing?" and "les pieds nickelés".

Then:

- `bundle exec nanoc` will build the site;
- `bundle exec nanoc deploy` will deploy the site to the server hosting the site;
- the site can be previewed by launching a local server with

        bundle exec nanoc view -p 4000 > /path/to/my.log 2>&1 &

Several deployment method are supported, which can be configured in `nanoc.yaml`, in section `deploy`. The file `nanoc.yaml.in` has a commented out section for github: uncomment and fill in the details. I refer you to nanoc documentation for the extra steps needed to finish the setup, and also for other deployment methods.
