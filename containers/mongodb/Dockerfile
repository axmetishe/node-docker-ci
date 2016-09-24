FROM centos:latest
LABEL name="MongoDB 3.2"
COPY config/repo.list /etc/yum.repos.d/mongodb-org-3.2.repo
RUN yum install -y --disableplugin=fastestmirror mongodb-org-server && yum -y clean all
EXPOSE 27017
ENTRYPOINT ["/usr/bin/mongod"]
LABEL image.version="1.0"
LABEL build-date="2016-09-22"
