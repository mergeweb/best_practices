# Best Practices

A collection of best practices and wisdom nuggets, from and for the developers at Up&amp;Up.

 - [URLs](#urls)
 - [Local Dev](#local-dev)
 - [Deployment](#deployment)
  - [Staging](#staging)
  - [Production](#production)
 - [Other Notes](#other-notes)
 - [Todos](#todos)

## URLs

 - Live: http://bp.mergeweb.net
 - Local: http://127.0.0.1:4000/

## Local Dev
 1. Clone the repo into /var/www/websites/best_practices/app
 2. run `gem install jekyll bundler` to install jekyll
 3. run `bundle install` to install everything you need for this project
 4. run `bundle exec jekyll serve` to spin up a local version of the site at `http://127.0.0.1:4000/`

## Deployment

### Staging
 Just merge your changes into the master branch and `cap staging deploy`.

## Other Notes

Based on the Hyde theme. Hyde is a brazen two-column [Jekyll](http://jekyllrb.com) theme that pairs a prominent sidebar with uncomplicated content. It's based on [Poole](http://getpoole.com), the Jekyll butler.

## Todos
 - Make the theme github pages compatible.
