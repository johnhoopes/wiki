<!-- TITLE: Mobsf -->
<!-- SUBTITLE: A quick summary of Mobsf -->

# Static apk analysis
Highlights findings that you'd go have to investigate.

Note that setup.sh needs a handful of packages installed libxml-dev I think was one.  Once those are installed rerun setup.sh.  Building by hand was hard and I never worked it out.

# Run in a docker
Easiest way to run.
Get the docker file (currently on blue and green unix vms).

```
docker build .
```

Will make an ID... not sure how to get to these again.
6d326a1515ba - green 
blue failed!!!! not supposed to happen!!!!

```
docker run -ti -p 8000:8000 6d326a1515ba
```