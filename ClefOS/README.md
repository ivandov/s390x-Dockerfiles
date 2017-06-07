# ClefOS Dockerfile

This is a copy of the [sinenomine/clefos-base-s390x](https://hub.docker.com/r/sinenomine/clefos-base-s390x/) image on Docker Hub with the slight modification of enabling systemd as the container's PID 0.

This is necessary for certain middleware that requires systemd to be operational.

Running this image requires setting the "privileged" flag in order to enable systemd.


### Build
`docker build . -t s390x/clefos-systemd`

After building the image, `s390x/clefos-systemd` will now be able to be used as a base image in other Dockerfiles. 
