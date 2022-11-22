FROM ubuntu:18.04

# Install prerequisites
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    build-essential \
    cmake \
    curl \
    git \
    libcurl3-dev \
    libleptonica-dev \
    liblog4cplus-dev \
    libopencv-dev \
    libtesseract-dev \
    wget \
    openjdk-8-jdk \
    default-jdk

# Copy all data
COPY . /srv/openalpr
RUN export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
# Setup the build directory
RUN mkdir /srv/openalpr/src/build
WORKDIR /srv/openalpr/src/build

# Setup the compile environment
RUN cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_INSTALL_SYSCONFDIR:PATH=/etc .. && \
    make -j2 && \
    make install
    
COPY run.sh /data/
COPY sample.png /data/

RUN chmod +x /data/run.sh

WORKDIR /data

#CMD ["/bin/sh", "-c", "run.sh"]
#CMD ["alpr","sample.png","run.sh"]
#RUN chmod a+x ./run.sh
#ENTRYPOINT ["/bin/sh", "-c", "run.sh" ]
ENTRYPOINT ["alpr"]
