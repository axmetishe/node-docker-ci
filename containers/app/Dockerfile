FROM centos:latest
LABEL name="Meteor TODOList App"
ENV MONGO_URL "mongodb://mongodb:27017"
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
COPY config/ssh/id_rsa.pub /root/.ssh/authorized_keys
RUN chmod 700 /root/.ssh && chmod 600 /root/.ssh/authorized_keys
COPY config/repo.list /etc/yum.repos.d/nginx.repo
RUN yum install -y nginx iproute openssh-server g++ make && yum -y clean all
RUN cd /var/lib/ && curl https://nodejs.org/dist/v4.5.0/node-v4.5.0-linux-x64.tar.xz|tar xJ
RUN ln -s /var/lib/node-v4.5.0-linux-x64/bin/node /usr/local/bin/node
RUN ln -s /var/lib/node-v4.5.0-linux-x64/bin/npm /usr/local/bin/npm
RUN systemctl enable sshd nginx
CMD ["/usr/sbin/init"]
LABEL image.version="1.0"
LABEL build-date="2016-09-22"
