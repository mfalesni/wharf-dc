FROM centos:7

MAINTAINER Milan Falesnik



RUN yum -y install epel-release && yum clean all
RUN yum -y update && yum -y install python-pip git && yum clean all
RUN git clone https://github.com/seandst/webdriver-wharf.git /tmp/webdriver-wharf
RUN pip install -U pip setuptools psycopg2 appdirs "apscheduler>=3" "docker-py>=1.1" Flask pytz sqlalchemy

ADD check-same-thread.diff /tmp/webdriver-wharf/
RUN cd /tmp/webdriver-wharf && git apply check-same-thread.diff

RUN cd /tmp/webdriver-wharf && python setup.py install

EXPOSE 4899

CMD ["webdriver-wharf"]
