# Zepplin-Death-Cause-Detector
Using Zepplin and Spark

**Zeppelin**, a web-based notebook that enables interactive data analytics. You can make beautiful data-driven, interactive and collaborative documents with SQL, Scala and more.

Core feature:
   * Web based notebook style editor.
   * Built-in Apache Spark support

## Requirements
 * Java 1.7
 * Tested on Mac OSX, Ubuntu 14.X, CentOS 6.X
 * Maven (if you want to build from the source code)
 * Node.js Package Manager

## Getting Started

### Before Build
If you don't have requirements prepared, install it. 
(The installation method may vary according to your environment, example is for Ubuntu.)

```
sudo apt-get update
sudo apt-get install git
sudo apt-get install openjdk-7-jdk
sudo apt-get install npm
sudo apt-get install libfontconfig

# install maven
wget http://www.eu.apache.org/dist/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz
sudo tar -zxf apache-maven-3.3.3-bin.tar.gz -C /usr/local/
sudo ln -s /usr/local/apache-maven-3.3.3/bin/mvn /usr/local/bin/mvn
```

_Notes:_ 
 - Ensure node is installed by running `node --version`  
 - Ensure maven is running version 3.1.x or higher with `mvn -version`

### Build
Steps to clone Zepplin from starting :
```
# basic build
mvn clean package -Pspark-1.6 -Phadoop-2.4 -Ppyspark

.....


#### Ignite Interpreter

```
mvn clean package -Dignite.version=1.1.0-incubating -DskipTests
```

#### Scalding Interpreter

```
mvn clean package -Pscalding -DskipTests
```

### Configure
If you wish to configure Zeppelin option (like port number), configure the following files:

```
./conf/zeppelin-env.sh
./conf/zeppelin-site.xml
```
(You can copy ```./conf/zeppelin-env.sh.template``` into ```./conf/zeppelin-env.sh```. 
Same for ```zeppelin-site.xml```.)


#### Setting SPARK_HOME and HADOOP_HOME

Without SPARK_HOME and HADOOP_HOME, Zeppelin uses embedded Spark and Hadoop binaries that you have specified with mvn build option.
If you want to use system provided Spark and Hadoop, export SPARK_HOME and HADOOP_HOME in zeppelin-env.sh
You can use any supported version of spark without rebuilding Zeppelin.

```
# ./conf/zeppelin-env.sh
export SPARK_HOME=...
export HADOOP_HOME=...
```


### Run
    ./bin/zeppelin-daemon.sh start

    browse localhost:8080 in your browser.


For configuration details check __./conf__ subdirectory.

### Package
To package the final distribution including the compressed archive, run:

      mvn clean package -Pbuild-distr

