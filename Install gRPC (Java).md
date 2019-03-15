# 安装 gRPC-java (Java)

环境:

* 系统: Ubuntu Desktop 18.04.1 LTS
* 语言: Java

```bash
# 安装 OpenJDK 8
sudo apt-get update
sudo apt-get install openjdk-8-jdk

# 安装 SDKMAN!
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"

# 安装 Gradle
sdk install gradle 5.2.1

# 拉取 grpc-java
git clone https://github.com/grpc/grpc-java.git
cd grpc-java/compiler

# 这一步可能需要科学上网
../gradlew java_pluginExecutable
../gradlew test
```

