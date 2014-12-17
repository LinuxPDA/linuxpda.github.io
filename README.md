linuxpda.github.io
==================

This is a source of Linux on PDA project website. If you'd like to add
or extend information about any of the handheld/palmtop/pocket/wearable
devices supported under Linux, please send us a pull request.

Device Files
------------
Each device or a series of similar devices are described in a separate
file. These files are stored under _devices/<vendor>/<family>/ hierarchy.
The file can be written using Markdown or raw HTML. Both types of files
will be processed by the site engine to create a per-device page. The
device file should use the template below:
```md
---
layout: device
vendor: HP
model: Jornada 720
status-boot: Y
status-boot-comment: Works
status-basic: Y
... more status lines...
---

**Text about device comes after second line with three dashes.**
```

Local testing
-------------
The following commands represent an easy way to check your modifications
locally:

* Install bundler Ruby dependencies manager (using your distro tools).
* Go to the directory with checked out copy of the site.
* Run ```bundle install```
* Run ```bundle exec jekyll serve```
* Navigate your favourite browser to http://localhost:4000/

If you change or add any of the files inside the directory with the
site sources, running Jekyll server will automatically regenerate
dependent pages. The only exception being a configuration file --- *_config.yml*.

