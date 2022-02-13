FROM ubuntu:20.04
MAINTAINER Shawn Milochik <shawn@milochik.com>
ENV DEBIAN_FRONTEND noninteractive
ENV REFRESHED_AT 2014-08-12b
RUN apt-get update
RUN apt-get install python3-pip -y
ADD ./provision /src/provision
WORKDIR /src
RUN /bin/bash /src/provision/debian.sh
ADD ./requirements /src/requirements
RUN /bin/bash /src/provision/python3.sh
ADD . /src
RUN adduser --disabled-password --gecos "" --home=/home/textract textract
VOLUME ["/home/textract/src"]
ENV PATH $PATH:/home/textract/src/bin
ENV PYTHONPATH /home/textract/src
USER textract
ENTRYPOINT ["/home/textract/src/tests/run.py"]
