# This is an auto generated Dockerfile for gazebo:gzweb7
# generated from templates/docker_images/create_gzweb_image.Dockerfile.em
# generated on 2016-09-26 17:45:00 +0000
FROM gazebo:libgazebo7
MAINTAINER Steven Peters scpeters+buildfarm@osrfoundation.org

# install packages
RUN apt-get update && apt-get install -q -y \
    build-essential \
    cmake \
    imagemagick \
    libboost-all-dev \
    libgts-dev \
    libjansson-dev \
    libtinyxml-dev \
    mercurial \
    nodejs \
    nodejs-legacy \
    npm \
    pkg-config \
    psmisc\
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

# install gazebo packages
RUN apt-get update && apt-get install -q -y \
    libgazebo7-dev=7.3.1* \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

# clone gzweb
RUN hg clone https://bitbucket.org/osrf/gzweb ~/gzweb

# build gzweb
RUN cd ~/gzweb \
    && hg up default \
    && ./deploy.sh -m

# setup environment
EXPOSE 8080
EXPOSE 7681

# run gzserver and gzweb
CMD ./root/gzweb/start_gzweb.sh && gzserver
