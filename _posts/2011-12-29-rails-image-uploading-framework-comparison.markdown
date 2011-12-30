---
layout: post
title: Rails comparison: CarrierWave vs. Paperclip vs. Dragonfly
published: true
categories: [tricks, fixes]
---

# Which should you use -- CarrierWave, Paperclip or Dragonfly?

Cloud-based storage has become incredibly cheap. Rails plugins like [fog](https://github.com/fog/fog) give you stupid simple cloud service integration. It's no wonder there are some great libraries for integrating image manipulation with cloud uploading.

## Motivation

This winter break, I'm hacking on a mongodb-backed refresh of [GifURl](http://gifurl.com "GifURL"), my handy-dandy database of user-uploaded gifs. One of the important features of GifURL is its ability to take a user's submitted gif URL (or entire page of scrape-able gifs) and ensure it is safely hosted for the future.

In my previous iteration, I wrote a [couple of functions](https://github.com/bcjordan/gifurl/blob/master/app/models/gif.rb#L63) to host images on [imgur](http://imgur.com) and fail back to [ehost](http://eho.st) which can support much larger gif file sizes (looking at you, animated gifs [made from YouTube videos](http://www.gifsoup.com/ "YouTube to Animated GIF website")).

This time, in addition to these fail-backs, GifURL will store backups of the submitted images on a remote server. In order to do this, we need two things -- a remote storage solution and  

# CarrierWave vs. Paperclip vs. Dragonfly comparison

This is a bit of a meta-review of comparisons of CarrierWave, Paperclip and Dragonfly.

## [CarrierWave](https://github.com/jnicklas/carrierwave)
### 2,494 watchers, 569 closed issues
From what I've read, CarrierWave is the most mature and full-featured image processing and uploading library out there for Rails 3. There is support for a number of object-relational mappers, including [carrierwave-mongoid](https://github.com/jnicklas/carrierwave-mongoid)

There is a nice [RailsCast on CarrierWave](http://railscasts.com/episodes/253-carrierwave-file-uploads "#253 CarrierWave File Uploads - RailsCasts"), which will give you a good idea of what's involved with implementing an upload view, form, controller and Uploader class and generating thumbnails for users' uploads with an [RMagick](https://github.com/rmagick/rmagick) transform.

It's also worth noting that CarrierWave has a Paperclip compatibility layer that lets you migrate your Paperclip-integrated app relatively painlessly. CarrierWave can now be used with mongo_mapper, though much of the mongo_mapper crowd has run off to use Dragonfly due to Carrierwave's late support.

There's also a nice [demo implementation](https://github.com/trevorturk/carrierwave-heroku/commit/606f4b3064fb1e370d2a0eae26cba7dd11231294) of using CarrierWave for avatar uploads targeting a Heroku deployment using s3 for storage (directly, without using [fog](https://github.com/fog/fog)).

## [Paperclip](https://github.com/thoughtbot/paperclip)
### 3,836 watchers, 639 closed issues

[Paperclip](https://github.com/thoughtbot/paperclip) is a file upload handling library built by the fine gents from Boston's ThoughtBot (of [Shoulda](https://github.com/thoughtbot/shoulda), [FactoryGirl](https://github.com/thoughtbot/factory_girl), and [apprentice.io](http://apprentice.io) fame). 

Paperclip has long been **the** way to implement cloud-backed file uploads in Rails. It has some seriously convenient methods and ThoughtBot's code tends to be easy to read.

You can find tutorials on doing a lot of things with Paperclip, such as [using Delayed Job to queue up Amazon S3 uploads](http://codewordstudios.com/posts/3-delayed-upload-delivery-to-s3-with-paperclip-delayed-job) and [animated gif resizing](https://github.com/thoughtbot/paperclip/pull/454) seems to be simpler now.

## [Dragonfly](http://markevans.github.com/dragonfly/file.Index.html)
### 746 watchers, 149 closed issues

Dragonfly is a relative newcomer, but there are some early signs it will be the way to go soon enough. Many mongo_mapper users have moved to it as Dragonfly supports mongomapper by default.

There are special instructions for using [Dragonfly on Heroku](http://markevans.github.com/dragonfly/file.Heroku.html)

# See also

* [CarrierWave or Dragonfly](http://stackoverflow.com/questions/3755662/carrierwave-or-dragonfly "ruby on rails - Carrierwave or Dragonfly - Stack Overflow") on StackOverflow
* [Paperclip vs. Carrierwave vs. Dragonfly vs. attachment_fu](http://stackoverflow.com/questions/7419731/rails-3-paperclip-vs-carrierwave-vs-dragonfly-vs-attachment-fu) on StackOverflow
* [Discussion in comments](http://thinkvitamin.com/code/10-must-have-ruby-gems/#comments "10 Must Have Ruby Gems | Think Vitamin") of 10 must have ruby gems on ThinkVitamin
