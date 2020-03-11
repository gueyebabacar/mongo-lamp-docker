FROM jenkins/jenkins:lts

LABEL maintainer="Antoine Descamps <antoine.descamps@ineat-conseil.fr>"
USER root
RUN echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list \
    && apt-key adv --keyserver https://keyserver.ubuntu.com:443 --recv-keys 93C4A3FD7BB9C367
RUN apt-get update

# Install OpenJDK-8
RUN apt-get install -y openjdk-8-jdk && \
    apt-get install -y ant && \
    apt-get clean;

# Fix certificate issues
RUN apt-get install ca-certificates-java && \
    apt-get clean && \
    update-ca-certificates -f;

# Setup JAVA_HOME -- useful for docker commandline
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/
RUN export JAVA_HOME

# install maven
RUN apt-get install maven -y

RUN curl -fsSL https://get.docker.com | bash - \
    && curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-Linux-x86_64" -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose
RUN usermod -aG docker jenkins

USER jenkins