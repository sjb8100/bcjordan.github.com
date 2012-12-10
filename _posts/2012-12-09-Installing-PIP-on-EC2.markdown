---
layout: post
title: Installing python pip on Amazon EC2 images
published: true
categories: [tricks]
permalink: pip-on-amazon-ec2
---

Amazon's EC2 image has yum, rpm installations, and the other niceities of Red Hat / Fedora brand Linux, and lightning fast local repo access.

Unfortunatley, pip doesn't seem to be in the repo.

Useful pastable pip build + installation comands from [this blog](http://somequantstuff.wordpress.com/2012/08/07/installing-scipy-for-python-on-amazon-linux-ec2/):

    wget http://pypi.python.org/packages/source/p/pip/pip-1.1.tar.gz#md5=62a9f08dd5dc69d76734568a6c040508
    tar -xvf pip*.gz
    cd pip*
    sudo python setup.py install

Works like a charm.

![](http://gifsoup.com/webroot/animatedgifs/465088_o.gif)