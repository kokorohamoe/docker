#
#
#FROM busybox
FROM centos

RUN yum -y install wget
RUN wget https://archive.cloudera.com/cdh5/one-click-install/redhat/7/x86_64/cloudera-cdh-5-0.x86_64.rpm

RUN rpm -ivh cloudera-cdh-5-0.x86_64.rpm

ADD core-site.xml /etc/hadoop/conf/

RUN yum repolist

RUN yum -y install sudo

RUN yum -y install java-1.8.0-openjdk-devel
RUN export JAVA_HOME=/usr/lib/jvm/jre-1.8.0/
RUN java -version

RUN yum -y install hadoop
RUN yum -y install hadoop-hdfs-namenode
RUN yum -y install hadoop-hdfs-datanode
RUN yum -y install hadoop-conf-pseudo

RUN hadoop namenode -format
RUN ip -f inet -o addr show docker0|cut -d\  -f 7 | cut -d/ -f 1 > name.host

RUN chown root /var/run/hadoop-hdfs

RUN echo "#!/usr/bin/bash" > service
RUN echo "/usr/bin/hadoop namenode 2>&1 &" >> service
#RUN echo "/usr/bin/hadoop datanode 2>&1 &" >> service 
RUN echo "ps -ef | grep hadoop" >> service
#RUN echo "/usr/bin/bash" >> service
#RUN /usr/bin/bash service > /var/log/hadoop.log

RUN echo "#!/usr/bin/bash" > entrypoint
RUN echo " /usr/bin/hadoop datanode 2>&1 >  namenode.log" >> entrypoint
RUN echo "/usr/bin/bash" >> entrypoint
RUN chmod +x entrypoint

ENTRYPOINT /usr/bin/bash entrypoint

#ENTRYPOINT  /usr/bin/hadoop namenode 2>&1 > /dev/null
#CMD /usr/bin/bash entrypoint

#
#
