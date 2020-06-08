This repository contains all that is needed to fully generate the [Knowledge Base](https://www.yathit.com/gmail-addon/overview.html) for [Yathit Mobile App for Sugar/SuiteCRM](https://www.yathit.com/suitecrm-mobile-app/index.html).

For this opensource Knowledge Base web site generator, see : [Lessons Learned Building a Git-Based Knowledge Base for my SaaS product](https://www.wisecashhq.com/blog/lessons-learned-creating-a-git-based-knowledge-base-for-my-saas-product).


## How to run locally

* Clone this repository to your machine.
* Make sure to have Ruby installed (tested fine on Ruby 2.3.x).
* Install required dependencies with `bundle install`
* Run

    jekyll serve --watch
    
For Windows machine, start Ubuntu for bash, install jekyll and go to before starting. 

    cd /mnt/c/Users/mbikyaw/WebstormProjects/yathit-for-sugar-doc
    

* Go to [http://localhost:4000/gmail-addon/](http://127.0.0.1:4000/gmail-addon/)

## Images

Resizing screenshots,

    sips -Z 466 *.png

    sips -Z 466  ~/screenshot/*.png    

In windows, `choco install ImageMagick`.

    magick mogrify -resize  360x *.png
    
Resize gif

    gifsicle --colors 256 --resize-fit-width 360 -i  animation.gif -o animation-360px.gif        

Uploading

    gsutil -m rsync -r ~/screenshot gs://yathit-assets/addon
    rm ~/addon/*

Or

    gsutil mv *.png  gs://yathit-assets/addon/

List files

    gsutil ls gs://yathit-assets/addon/*
    

To use the image as centered.

    ![centered-image](https://yathit-assets.storage.googleapis.com/screencast/addon/other-recipients.gif)

   

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
    
## Deploy

Then, to publish quickly as latest version

    (cd ~/gae/yathit-app; mvn appengine:deploy -Dapp.deploy.version=addon-doc)
