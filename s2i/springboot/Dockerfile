# tomcat
FROM  docker.io/wuxinbo/springboot:1.0 

# TODO: Put the maintainer name in the image metadata
MAINTAINER wuxinbo wuxb@ect888.com

# TODO: Rename the builder environment variable to inform users about application you provide them

# TODO: Set labels used in OpenShift to describe the builder image
#LABEL io.k8s.description="Platform for building xyz" \
LABEL  io.openshift.s2i.destination="/home/wuxinbo/app" \
			 io.openshift.s2i.scripts-url="image:///usr/libexec/s2i" 
#      io.k8s.display-name="builder x.y.z" \
#      io.openshift.expose-services="8080:http" \
#      io.openshift.tags="builder,x.y.z,etc."
# TODO: Install required packages here:
# RUN yum install -y ... && yum clean all -y

# 创建应用目录
RUN mkdir -p /home/wuxinbo/app
# TODO (optional): Copy the builder files into /opt/app-root
#COPY ./<builder_folder>/ /opt/app-root/

# TODO: Copy the S2I scripts to /usr/libexec/s2i, since openshift/base-centos7 image
# sets io.openshift.s2i.scripts-url label that way, or update that label

# TODO: Drop the root user and make the content of /opt/app-root owned by user 1001
RUN chown -R 1001:1001 /home/wuxinbo/app
RUN chown -R 1001:1001 /home/wuxinbo/maven-repo

# This default user is created in the openshift/base-centos7 image
USER 1001

# TODO: Set the default port for applications built using this image
EXPOSE 8080
ENV HOME=/home/wuxinbo/app
ENV APP_NAME=agent-api
WORKDIR $HOME
COPY ./s2i/bin/ /usr/libexec/s2i
# TODO: Set the default CMD for the image
CMD /bin/bash
# CMD ["/usr/libexec/s2i/usage"]
