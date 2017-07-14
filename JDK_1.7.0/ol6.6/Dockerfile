# NAME:
#   Dockerfile
#
# DESC:
#   Dockerfile for building a Docker container which contains the
#   OpenJDK 1.7.0. This container will be based upon the Oracle
#   Linux container. 
#
# LOG:
# VERSION---DATE--------NAME-------------COMMENT
# 0.1       13JUL17     Johan Louwers    Initial upload to github.com
# 0.2 .     14JUL17     Johan Louwers    Added fix for Docker bug 10180
#
# LICENSE:
# Copyright (C) 2015  Johan Louwers
#
# This code is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This code is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this code; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  
# 02110-1301, USA.
# *
# */

FROM oraclelinux:6.6

MAINTAINER Johan Louwers <louwersj@gmail.com>
LABEL maintainer="louwersj@gmail.com"

# Parse arguments for the build command.
ARG VERSION
ARG VCS_URL
ARG VCS_REF
ARG BUILD_DATE

# A little bit of metadata management.
# See http://label-schema.org/
LABEL org.label-schema.schema-version="1.0" \
      org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.vendor="louwersj@gmail.com" \
      org.label-schema.version=$VERSION \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.name="openJDK" \
      org.label-schema.description="Java OpenJDK 1.7.0 on Oracle Linux 6"

# Adding a rpm --rebuildddb prior to the yum install 
# as a fix for Docker bug 10180
RUN rpm --rebuilddb
RUN touch /var/lib/rpm/*

RUN yum -y install java-1.7.0-openjdk-devel && yum clean all

ENV JAVA_HOME /usr/lib/jvm/java-openjdk

CMD ["java", "-version"]
