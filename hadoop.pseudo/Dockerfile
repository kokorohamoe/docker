#
#
#FROM busybox
FROM centos

RUN yum -y install wget
RUN wget https://archive.cloudera.com/cdh5/one-click-install/redhat/7/x86_64/cloudera-cdh-5-0.x86_64.rpm

RUN rpm -ivh cloudera-cdh-5-0.x86_64.rpm

RUN yum repolist

RUN yum -y install sudo

RUN yum -y install java-1.8.0-openjdk-devel
RUN export JAVA_HOME=/usr/lib/jvm/jre-1.8.0/
RUN java -version

RUN yum -y install hadoop
RUN yum -y install hadoop-hdfs-namenode
RUN yum -y install hadoop-conf-pseudo

RUN hadoop namenode -format
RUN ip -f inet -o addr show docker0|cut -d\  -f 7 | cut -d/ -f 1 > name.host

ENTRYPOINT /usr/bin/hadoop namenode
#
#
