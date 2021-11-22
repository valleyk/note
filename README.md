<!-- 
## index


centos查看防火墙服务状态

```
systemctl status firewalld
```

查看firewall的状态

```
firewall-cmd --state
```

```
# 开启
service firewalld start
# 重启
service firewalld restart
# 关闭
service firewalld stop
```

```
# 查看防火墙规则
firewall-cmd --list-all 
```


> hyper-v centos docker install

```url
https://www.cnblogs.com/yazid/p/12772617.html
```



> centos install gradle

```
https://cloud.tencent.com/developer/article/1137642
```

```shell
# vi /etc/profile.d/gradle.sh
export GRADLE_HOME=/usr/local/software/gradle/gradle720
export PATH=$PATH:$GRADLE_HOME/bin
```

```shell
source /etc/profile
```

> centos install jdk

```shell
vi /etc/profile.d/jdk.sh
export JAVA_HOME=/usr/local/software/jdk/java/jdk180
export PATH=$PATH:$JAVA_HOME/bin
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

```



> centos install maven

```
https://maven.apache.org/download.cgi
```

```shell
wget https://dlcdn.apache.org/maven/maven-3/3.8.3/binaries/apache-maven-3.8.3-bin.zip --no-check-certificate
```



```shell
# vi /etc/profile.d/maven.sh
MAVEN_HOME=/usr/local/software/maven383
export PATH=${MAVEN_HOME}/bin:${PATH}
```





```
sudo yum remove docker \
　　docker-client \
　　docker-client-latest \
　　docker-common \
　　docker-latest \
　　docker-latest-logrotate \
　　docker-logrotate \
　　docker-engine
```

```
rm /var/lib/docker
```



```
https://docs.docker.com/engine/install/centos/
```

```shell
sudo yum install -y yum-utils
```

```shell
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

```shell
/etc/yum.repos.d/docker-ce.repo
```

> Install the *latest version* of Docker Engine and container, or go to the next step to install a specific version

```shell
sudo yum install docker-ce docker-ce-cli containerd.io
```

> install a specific version

```shell
yum list docker-ce --showduplicates | sort -r
```

```shell
sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
```



> start docker

```shell
sudo systemctl start docker
```



> centos  install jetbrains projector

[projector py installer](https://github.com/JetBrains/projector-installer)

```shell
sudo yum install python3 python3-pip pyOpenSSL python-cryptography -y
```

```shell
python3 -m pip install -U pip --user 
```

```shell
sudo yum install less libXext libXrender libXtst libXi freetype -y  
```

````shell
pip3 install projector-installer --user
````

```shell
source ~/.bash_profile
```

```shell
vi /etc/profile.d/projector.sh
export PATH=$PATH:/root/.local/bin:${PATH}
```

```shell
source /etc/profile
```

```
 ps aux | grep srs 

 netstat -lnp | grep srs 
```







[APT](https://blog.csdn.net/MaiDouYT/article/details/108046471)

关于在注解中使用配置文件中的配置？修改某一个类的staic变量 







spring  先构造器-> setApplicatonConext -> postConsturctor 

static变量可以被autowired 或者@ConfigurationProperty 或者@Value,前提是setter方法没有被static 修饰,使用@Value时，需要@Value在setter方法上，而不是变量上

//todo 分析原因，应该在@Value和@ConfigurationPropety的注释上



```
netsh interface portproxy add v4tov4 listenport=2375 listenaddress=192.168.1.31 connectport=2375 connectaddress=localhost
```





```
netsh interface  portproxy show  v4tov4netsh interface portproxy delete v4tov4 listenaddress=192.168.4.20  listenport=20002netsh interface portproxy add v4tov4 listenport=20002 listenaddress=192.168.4.20 connectport=22 connectaddress=192.168.127.100
```





```
http://192.168.4.20:9999/?ideWindow=0
```

```
http://192.168.4.20:9999/?ideWindow=1
```




```java
@Configuration
@ConfigurationProperties(prefix = "xx")
public class TestMethod implements ApplicationContextAware {
    
    private ApplicationContext applicationContext;
    
    private  ObjectMapper objectMapper;
    
    private static String a;
    private static String b;

    public  String getA() {
        return a;
    }

    public  void setA(String a) {
        TestMethod.a = a;
    }

    public  String getB() {
        return b;
    }

    public  void setB(String b) {
        TestMethod.b = b;
    }
    
    @PostConstruct
    public void init(){
        System.out.println("postconstructor");
        String property = applicationContext.getEnvironment().getProperty("xx.a");
        String property1 = applicationContext.getEnvironment().getProperty("xx.b");
        TestMethod bean = applicationContext.getBean(TestMethod.class);
        String a = bean.getA();
        String b = bean.getB();
        System.out.println(TestMethod.a);
        System.out.println(TestMethod.b);
    }

    public TestMethod(ObjectMapper objectMapper) {
        System.out.println(a);
        System.out.println(b);
        this.objectMapper = objectMapper;
    }

    public TestMethod() {
        System.out.println("constructor");
        System.out.println(a);
        System.out.println(b);
    }
    
    @Override
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
        this.applicationContext = applicationContext;
    }
}
```



webdav.exe -p 9999 --auth=false --tls=false
 -->
