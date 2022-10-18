FROM  centos:7
LABEL maintainer="revang.alternative@foxmail.com"

# 修改yum源
RUN mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
COPY application_data/yum/Centos-7.repo /etc/yum.repos.d/CentOS-Base.repo
RUN yum install -y vim unzip

# 安装JDK
# ADD application/jdk-8u341-linux-x64.tar.gz /usr/local/
# RUN mv /usr/local/jdk1.8.0_341 /usr/local/jdk
ADD application/jdk-7u80-linux-x64.tar.gz /usr/local/
RUN mv /usr/local/jdk1.7.0_80 /usr/local/jdk
ENV JAVA_HOME=/usr/local/jdk
ENV JRE_HOME=${JAVA_HOME}/jre
ENV CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH=${JAVA_HOME}/bin:$PATH

# 安装Tomcat
ADD application/apache-tomcat-7.0.100.zip /usr/local/
RUN cd /usr/local && unzip apache-tomcat-7.0.100.zip && rm -f apache-tomcat-7.0.100.zip && mv apache-tomcat-7.0.100 tomcat
RUN cd /usr/local/tomcat/bin && chmod a+x *.sh
ENV CATALINA_HOME=/usr/local/tomcat
ENV PATH=${CATALINA_HOME}/bin:$PATH

# 安装BSAML
RUN mkdir -p /usr/fundcrm/accessory
ADD application/fundcrm/bsaml.zip /usr/fundcrm
ADD application/fundcrm/etc.zip /usr/fundcrm
RUN cd /usr/fundcrm && unzip bsaml.zip && rm -f bsaml.zip
RUN cd /usr/fundcrm && unzip etc.zip && rm -f etc.zip

# 安装依赖
RUN yum install -y net-tools

# 修复中文乱码
RUN yum -y install kde-l10n-Chinese
RUN localedef -c -f UTF-8 -i zh_CN zh_CN.utf8
RUN echo LANG= " zh_CN.UTF-8 " >>/etc/locale.conf
ENV LC_ALL=zh_CN.UTF-8 

# 启动
EXPOSE 8888
# CMD ["bash"]
CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]


