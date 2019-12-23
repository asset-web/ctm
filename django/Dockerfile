from centos:7.7.1908

ENV PYTHONDONTWRITEBYTECODE=1

# Utilities
RUN yum -y install wget

# EPEL package repository and updates
RUN yum -y install epel-release
RUN yum -y update

# Python
RUN yum -y install https://centos7.iuscommunity.org/ius-release.rpm
RUN yum -y install python36u
RUN yum -y install python36u-setuptools
RUN yum -y install python36u-devel

RUN yum -y install gcc gcc-c++

# Install pip
RUN easy_install-3.6 pip

# PostgreSQL tools, ref versions https://www.postgresql.org/download/linux/redhat/
# Install the repository RPM
RUN yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
# Install the client packages
RUN yum -y install postgresql12
RUN yum -y install postgresql-devel

RUN pip install virtualenv
WORKDIR /srv
RUN virtualenv check_the_map

WORKDIR /srv/check_the_map
RUN ./bin/pip install --upgrade pip==19.3.1
RUN ./bin/pip install setuptools==42.0.2

COPY requirements.txt src/ctm/requirements.txt
RUN ./bin/pip install -r src/ctm/requirements.txt
COPY . src/ctm/

WORKDIR /srv/check_the_map/src/ctm