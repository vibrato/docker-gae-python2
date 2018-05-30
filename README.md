GAE Python Image
=================

For testing applications running on Google's App Engine you need to have python
configured with the google-cloud-sdk. Annoyingly these libraries are not
something that can be pip installed like other dependencies, they must be
installed into the OS.

This is simply a python 2.7 image with google-cloud-sdk installed and the
PYTHONPATH set up so that the base modules can be imported. We need this as a
docker container for CI systems such as CircleCI or bitbucket pipelines where
we provide our own runtime.

Usage
=====

Almost certainly the first thing you are going to want to do in python is:

```python
>>> import dev_appserver
>>> dev_appserver.fix_sys_path()
```

to fix the path to include the rest of the google specific libraries. It's so
common in fact that we should probably do it in the image - but that wouldn't
work very well with our existing tests so for now we just set up PATH so we can
import dev_appserver.
