FROM mesosphere/mesos:0.25.0-0.2.70.ubuntu1404

RUN apt-get update && apt-get install -y software-properties-common

RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer

ADD ./build/docker/mesos-hello-world-scheduler.jar /tmp/mesos-hello-world-scheduler.jar
ADD ./build/docker/start-scheduler.sh /tmp/start-scheduler.sh

ENTRYPOINT ["/tmp/start-scheduler.sh"]
