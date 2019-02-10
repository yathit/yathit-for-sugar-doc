This repository contains all that is needed to fully generate the [Knowledge Base](https://www.yathit.com/gmail-addon/overview.html) for [Yathit Mobile App for Sugar/SuiteCRM](https://www.yathit.com/suitecrm-mobile-app/index.html).

For this opensource Knowledge Base web site generator, see : [Lessons Learned Building a Git-Based Knowledge Base for my SaaS product](https://www.wisecashhq.com/blog/lessons-learned-creating-a-git-based-knowledge-base-for-my-saas-product).


## How to run locally

* Clone this repository to your machine.
* Make sure to have Ruby installed (tested fine on Ruby 2.3.x).
* Install required dependencies with `bundle install`
* Run

    jekyll serve --watch

* Go to [http://localhost:4000/gmail-addon/](http://127.0.0.1:4000/gmail-addon/)

## Images

Resizing screenshots,

    sips -Z 466 *.png

    sips -Z 466  ~/screenshot/*.png

In windows, `choco install ImageMagick`.

    magick mogrify -resize  360x *.png

Uploading

    gsutil -m rsync -r ~/screenshot gs://yathit-assets/screenshot
    rm ~/screenshot/*

Or

    gsutil mv *.png  gs://yathit-assets/addon/

List files

    gsutil ls gs://yathit-assets/addon/*

## How to build in production

This is mostly:

    ant

To build the site

    bundle exec jekyll build --destination ~/gae/yathit-app/src/main/webapp/static/gmail-addon

In windows, use bash for ubuntu to build the site

    cd //mnt/c/Users/mbikyaw/WebstormProjects/yathit-for-sugar-doc
    jekyll build
    
Then go back to PowerShell to copy files to destination folder
     
    ant copy
