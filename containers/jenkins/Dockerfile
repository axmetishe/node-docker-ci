FROM jenkins
LABEL name="Jenkins Server"
ENV JAVA_OPTS=-Djenkins.install.runSetupWizard=false
USER root
RUN apt-get update && apt-get install -y rpm make file gcc g++ build-essential && apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN curl https://install.meteor.com/ | sh
RUN cd /var/lib/ && curl https://nodejs.org/dist/v4.5.0/node-v4.5.0-linux-x64.tar.xz|tar xJ
ENV PATH "$PATH:/var/lib/node-v4.5.0-linux-x64/bin"
RUN npm install -g gagarin
USER jenkins
RUN /usr/local/bin/install-plugins.sh git:3.0.0 publish-over-ssh:1.14
LABEL image.version="1.0"
LABEL build-date="2016-09-23"
