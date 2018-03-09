# 开始
- java 安装
```
# install jdk1.8
- name: unpack java1.8 tar to remote
  unarchive: src=server-jre-8u144-linux-x64.tar.gz dest=/tmp

- name: install java
  shell: "{{ item }}"
  with_items:
    - sudo mkdir -p /usr/lib/jvm
    - sudo mv /tmp/jdk1.8.0_144 /usr/lib/jvm/
    - test -f /usr/bin/java && sudo rm /usr/bin/java
    - test -f /usr/bin/javac && sudo rm /usr/bin/javac
    - test -f /etc/alternatives/java && sudo rm /etc/alternatives/java
    - test -d /usr/lib/jvm/jdk1.8.0_111 && rm -rf /usr/lib/jvm/jdk1.8.0_111
    - sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0_144/bin/java" 1
    - sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0_144/bin/javac" 1
    - sudo chmod a+x /usr/bin/java
    - sudo chmod a+x /usr/bin/javac
    - sudo chown -R root:root /usr/lib/jvm/jdk1.8.0_144
    - sudo update-alternatives --config java
``` 

```
JobConf conf = new JobConf(new Configuration()); 
```
- [易百教程](https://www.yiibai.com/hadoop/hadoop_big_data_solutions.html)
- [w3school](https://www.w3cschool.cn/hadoop/xvmi1hd6.html)
- [Apache Hadoop 入门教程](https://waylau.com/about-hadoop/)
- [官方文档](https://hadoop.apache.org/docs/r1.0.4/cn/hdfs_shell.html)
