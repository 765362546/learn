FROM ubuntu
MAINTAINER malei

# ����Դ����װssh server
RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe"> /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y openssh-server
RUN mkdir -p /var/run/sshd
RUN mkdir -p /root/.ssh
RUN  /usr/bin/ssh-keygen -A
# ����root sshԶ�̵�¼����Ϊ123456
RUN echo "root:123123" | chpasswd

RUN sed -i "s/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config
RUN sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config
RUN sed -i 's/^PermitRootLogin without-password/PermitRootLogin yes/g' /etc/ssh/sshd_config

# ȡ��PAM����
RUN sed -i '/pam_loginuid.so/c session    optional     pam_loginuid.so'  /etc/pam.d/sshd

# ����orache java7Դ��һ���԰�װvim��wget��curl��java7��tomcat7�ȱر�����
# RUN apt-get install python-software-properties
# RUN add-apt-repository ppa:webupd8team/java
# RUN apt-get update
# RUN apt-get install -y vim wget curl oracle-java7-installer tomcat7
# ����JAVA_HOME��������RUN update-alternatives --display java
# RUN echo "JAVA_HOME=/usr/lib/jvm/java-7-oracle">> /etc/environment
# RUN echo "JAVA_HOME=/usr/lib/jvm/java-7-oracle">> /etc/default/tomcat7
# ������Ҫ����SSH 22�˿�
EXPOSE 22
# ������Ҫ����Tomcat 8080�˿�
# EXPOSE 8080
# ����Tomcat7��ʼ�����У�SSH�ն˷�������Ϊ��̨����
# ENTRYPOINT service tomcat7 start && /usr/sbin/sshd -D
ENTRYPOINT  /usr/sbin/sshd -D