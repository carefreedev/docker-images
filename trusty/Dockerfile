# CareFREE Docker image FROM ubuntu:trusty
#
# Copyright (C) 2016 Stefan Zimmermann <zimmermann.code@gmail.com>
#
# Licensed under the Apache License, Version 2.0

FROM ubuntu:trusty

RUN apt-get update
RUN apt-get dist-upgrade --yes --auto-remove --purge
RUN apt-get install --yes \
        gcc g++ gfortran gdb \
        make automake autoconf libtool \
        libboost-all-dev \
        python-dev python3-dev \
        snmp libsnmp-dev \
        bash git

RUN apt-get clean

ADD https://bootstrap.pypa.io/get-pip.py /

RUN python3 /get-pip.py
RUN python /get-pip.py

RUN pip install zetup[commands]

RUN mkdir /git

RUN git clone https://github.com/zimmermanncode/zcons.git /git/zcons
RUN cd /git/zcons && zetup install

RUN git clone https://github.com/carefreedev/carefree-objects.git /git/cfo
ENV CXXFLAGS="-std=c++11" LDFLAGS="-pthread"
RUN cd /git/cfo && zetup install
