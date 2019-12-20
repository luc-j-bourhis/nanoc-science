# Introduction

An infrastructure built around nanoc to produce contents on the web with a lot of maths and a heavy academic undertone (citations, etc).

# How to setup the build environment?

Ruby is the main dependency, as nanoc is written in that language. The exact version of ruby guaranteed to work is specified in the Gemfile as well as in a .ruby-version for users of rb-env. Eventually, the whole setup boils down to: `bundler install`. If you don't have the right version of ruby, this will fail and complain. Otherwise, all necessary packages will be installed and setup.

# How to build the site?

First clone this repository. Then create one directory in the `content` directory for each language in which you plan to write articles. Currently, only English and French are supported, directories `en` and `fr` respectively. Then each article shall live inside its own directory within its language directory: its content shall come from a file `index.md` written in markdown (the Kramdown flavour enhanced with features discussed below). Here is an example of hierarchy:

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

        bundle exec nanoc view -p 4000 > /tmp/luc-j-bourhis-github-io.log 2>&1 &
in `bash` or

        bundle exec nanoc view -p 4000 > /tmp/luc-j-bourhis-github-io.log ^&1 &
in `fish`.

Several deployment method are supported, which can be configured in `nanoc.yaml`, in section `deploy`. A fresh clone comes configured for github, for my own github account, so you will need to change the `remote` field. I refer you to nanoc documentation for the extra steps needed to finish the setup, and also for other deployment methods. In the future, I will provide a more user-friendly way to configure deployment out of the box!

