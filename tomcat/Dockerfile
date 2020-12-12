#基本镜像
FROM centos

#维护人信息，产品信息，描述信息等
LABEL version="1.0" description="tomcat Dockerfile" by="imliwenli"

#将本地（/home/liwenli/tomcat目录）的readme.txt拷贝到容器
COPY readme.txt /usr/local/readme.txt

#将本地（/home/liwenli/tomcat目录）的jdk压缩包添加到容器
ADD jdk-8u271-linux-x64.tar.gz /usr/local/

#将本地（/home/liwenli/tomcat目录）的tomcat压缩包添加到容器
ADD apache-tomcat-9.0.40.tar.gz /usr/local/

#centos镜像中没有vim包，执行安装vim的命令
RUN dnf install -y vim

#配置环境变量 
ENV LOCAL_PATH=/usr/local JAVA_HOME=/usr/local/jdk1.8.0_271 CLASS_PATH=$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar CATALINA_HOME=/usr/local/apache-tomcat-9.0.40 CATALINA_BASE=/usr/local/apache-tomcat-9.0.40 PATH=$PATH:JAVA_HOME/bin:$CATALINA_HOME/lib:$CATALINA_HOME/bin

#为构建的镜像设置监听端口，使容器在运行时监听
EXPOSE 80/tcp
EXPOSE 80/udp

#指定在容器启动时所要执行的命令
CMD /usr/local/apache-tomcat-9.0.40/bin/startup.sh && tail -F /usr/local/apache-tomcat-9.0.40/bin/logs/catalina.out 
