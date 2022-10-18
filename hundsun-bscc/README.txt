容器目录结构
usr
├── local
|   ├── java
|   └── tomcat
└── fundcrm
    ├── etc
    ├── bscc 
    └── accessory

调试
CMD /bin/bash
docker build -t hundsun-bscc .
docker run -it --privileged=true hundsun-bscc /bin/bash
/usr/local/tomcat/bin/catalina.sh run 

编译
docker build -t hundsun-bscc .

运行
docker run -d -p 7001:7001 --mac-address=00:02:02:03:18:F0 --name hundsun-bscc hundsun-bscc
