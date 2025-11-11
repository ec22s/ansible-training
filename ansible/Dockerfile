# CentOS7
FROM centos:7

# Use vault repositories
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

# install sudo
RUN yum -y install sudo
# install ssh clients
RUN yum -y install openssh-clients

# install ansible
RUN yum -y install epel-release && \
yum -y install ansible && \
yum clean all

# setttings
ADD ansible.cfg /etc/ansible