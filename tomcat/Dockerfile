#jdk+tomcat
#/opt/tomcat
FROM centos:6

ENV CATALINA_HOME /opt/tomcat


# INSTALL JAVA_HOME
RUN yum install -y wget tar java-1.6.0-openjdk

# INSTALL TOMCAT
RUN  cd /opt/ && \
wget http://mirrors.noc.im/apache/tomcat/tomcat-6/v6.0.44/bin/apache-tomcat-6.0.44.tar.gz && \
tar -vxf apache-tomcat-*.gz && \
rm -rf *.gz && \
mv apache-tomcat-* tomcat

ADD create_tomcat_admin_user.sh /create_tomcat_admin_user.sh
ADD run.sh /run.sh
RUN chmod +x /*.sh

EXPOSE 8080
CMD ["/run.sh"]