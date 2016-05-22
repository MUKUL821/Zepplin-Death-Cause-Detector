# Zeppelin-Death-Cause-Detector
Using Zeppelin and Spark

**Zeppelin**, a web-based notebook that enables interactive data analytics. You can make beautiful data-driven, interactive and collaborative documents with SQL, Scala and more.

Feature:
   * Web based notebook style editor.
   * It is built-in Apache Spark support

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


### Build
Steps to clone Zepplin from starting :
```
# basic build

mvn clean package -Pspark-1.6 -Phadoop-2.4 -Ppyspark

```
### Ignite Interpreter
```
mvn clean package -Dignite.version=1.1.0-incubating -DskipTests
```

### Scalding Interpreter

```
mvn clean package -Pscalding -DskipTests
```

###Configure
If you wish to configure Zeppelin option (like port number), configure the following files:

```
./conf/zeppelin-env.sh
./conf/zeppelin-site.xml
```


### Setting SPARK_HOME and HADOOP_HOME

Without SPARK_HOME and HADOOP_HOME, Zeppelin uses embedded Spark and Hadoop binaries that you have specified with mvn build option.
If you want to use system provided Spark and Hadoop, export SPARK_HOME and HADOOP_HOME in zeppelin-env.sh


```
### ./conf/zeppelin-env.sh
export SPARK_HOME=...
export HADOOP_HOME=...
```


### Run
    ./bin/zeppelin-daemon.sh start

    Browse localhost:8080 in your browser.
### Import Notebook

```
Steps for importing Notebook note.json in local system and viewing the result are given in Notebook folder README.MD file ```
