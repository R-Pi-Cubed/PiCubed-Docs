---
layout: default
title: Install Java
nav_order: 4
description: How to install Java on your Raspberry Pi
---
```java -version```  

```sudo apt install openjdk-17-jre-headless```

```sudo update-alternatives --config java```

```sudo nano /etc/environment```

```JAVA_HOME="/usr/lib/jvm/java-17-openjdk-arm64"```

```source /etc/environment```

```echo $JAVA_HOME```