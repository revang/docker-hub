容器目录结构
usr
├── local
|   ├── java
|   └── tomcat
└── fundcrm
    ├── etc
    ├── bsaml 
    └── accessory

调试
CMD /bin/bash
docker build -t hundsun-bsaml .
docker run -it hundsun-bsaml /bin/bash
/usr/local/tomcat/bin/catalina.sh run 

编译
docker build -t hundsun-bsaml .

运行
docker run -d -p 8888:8888 --mac-address=00:02:02:03:18:F0 --name hundsun-bsaml hundsun-bsaml
