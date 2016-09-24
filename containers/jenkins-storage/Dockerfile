FROM centos:latest
LABEL name="Jenkins Storage"
ENV container docker
VOLUME ["/run", "/tmp"]
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in * ; do [ $i == "systemd-tmpfiles-setup.service" ] || rm -f $i; done;\
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*)
VOLUME [ "/sys/fs/cgroup" ]
LABEL name="Jenkins storage"
RUN useradd -m -d "/var/jenkins_home" -u 1000 -s /bin/bash jenkins
RUN mkdir -p /var/log/jenkins
RUN chown -R jenkins:jenkins /var/log/jenkins
RUN mkdir -p /var/jenkins_home/{.ssh,jobs}
COPY config/ssh/* /var/jenkins_home/.ssh/
COPY config/jhome/deploy.xml /var/jenkins_home/jobs/test_and_deploy/config.xml
COPY config/jhome/config.xml /var/jenkins_home/config.xml
COPY config/jhome/publish_over_ssh.xml /var/jenkins_home/jenkins.plugins.publish_over_ssh.BapSshPublisherPlugin.xml
RUN chown -R jenkins:jenkins /var/jenkins_home/ && chmod 700 ~jenkins/.ssh && chmod 600 ~jenkins/.ssh/*
USER jenkins
VOLUME ["/var/log/jenkins", "/var/jenkins_home"]
CMD ["/usr/sbin/init"]
LABEL image.version="1.0"
LABEL build-date="2016-09-22"
