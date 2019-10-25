FROM centos:centos6

RUN yum update -y \
 && yum install -y gcc openssl-devel bzip2-devel

WORKDIR /tmp
ADD https://www.python.org/ftp/python/3.6.6/Python-3.6.6.tgz /tmp

RUN tar xzf Python-3.6.6.tgz 

WORKDIR /tmp/Python-3.6.6
RUN ./configure --enable-optimizations \
 && make altinstall \
 && ln -sfn /usr/local/bin/python3.6 /usr/bin/python3.6 \
 && ln -sfn /usr/local/bin/python3.6 /usr/bin/python3

WORKDIR /tmp
COPY requirements.txt .
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
 && python3 get-pip.py \
 && pip3 install -r requirements.txt

WORKDIR /app

