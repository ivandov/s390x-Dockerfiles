# Jenkins 2.19.4 LTS release

Exposes ports 8080 and 50000 and mounts a volume at `/jenkins`

Port 8080 is the default Web UI ports
Port 50000 is the default slave agent port

`docker run -d -p 8080:8080 -p 50000:50000 -v ~/.jenkins:/jenkins ivandov/jenkins`
