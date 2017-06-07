# Copyright (c) 2015 IBM. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM sinenomine/clefos-base-s390x

MAINTAINER "Ivan Dovgan" <ivandov@us.ibm.com>

ENV container docker
WORKDIR /tmp

EXPOSE 80

# Enable systemd
VOLUME [ "/sys/fs/cgroup" ]
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

# Enable the EPEL repository
RUN yum -y install \
    deltarpm \

# Install the minimum packages.
RUN yum -y install \
    gcc \
    java-1.7.0-openjdk \
    initscripts  \
    libffi-devel \
    net-tools \
    openssl-devel \
    policycoreutils \
    python-pip


CMD ["/usr/sbin/init"]
