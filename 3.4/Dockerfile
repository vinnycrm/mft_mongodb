#
# MongoDB Dockerfile in centos image
#

# Pull base image
FROM vinnycrm/centos

# Maintener
MAINTAINER Vinaya C R M <vinay@shrigowri.com>

# Install MongoDB
RUN echo -e "[mongodb]\nname=MongoDB Repository\nbaseurl=https://repo.mongodb.org/yum/redhat/7/mongodb-org/3.4/`uname -m`/\ngpgcheck=0\nenabled=1" > /etc/yum.repos.d/mongodb.repo && \
    yum install -y mongodb-org && \
    yum update -y && \
    yum clean all && \
    chown -R mongod:mongod /var/lib/mongo

# Copy config mongodb
COPY etc/ /etc/

# User
USER mongod

# Mountable directories
VOLUME ["/var/lib/mongo"]

# Set the environment variables
ENV HOME /var/lib/mongo

# Working directory
WORKDIR /var/lib/mongo

ENTRYPOINT ["/bin/mongod"]
CMD ["-f", "/etc/mongod.conf"]

# Expose ports.
EXPOSE 27017
