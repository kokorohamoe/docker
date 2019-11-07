#
#
#FROM busybox
FROM centos

#COPY group /etc/group
#COPY passwd /etc/passwd
#COPY shadow /etc/shadow
#COPY sudoers /etc/sudoers


#RUN echo ec2-user:x:1000:1000:ec2-user:/home/ec2-user:/bin/bash >> /etc/passwd
#RUN echo docker:993:ec2-user >> /etc/group
#RUN echo ec2-user:1000:      >> /etc/group

RUN /usr/sbin/groupadd -g 993 docker
RUN /usr/sbin/useradd -u 1000 ec2-user
RUN /usr/sbin/usermod -aG docker ec2-user
RUN /usr/sbin/usermod -aG docker ec2-user



ENTRYPOINT []
#
#
