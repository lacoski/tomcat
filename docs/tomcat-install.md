# Cài đặt Tomcat 9.0
---
## Mục lục
[I. Chuẩn bị](#chuanbi)

[II. Cài đặt](#caidat)
- [Bước 1: Download package dạng `*.zip`](#buoc1)
- [Bước 2: Giải nén thư mục](#buoc2)
- [Bước 3: Setup thư mục lưu trữ Apache Tomcat](#buoc3)
- [Bước 4: Cấp quyền thực thi cho Script file](#buoc4)
- [Bước 5: Kiểm tra, khởi chạy dịch vụ](#buoc5)
- [Bước 6: Cấu hình base URL tomcat (docbase)](#buoc6)

<a name="chuanbi"></a>
## I. Chuẩn bị
### 1. Các chú ý khi cài đặt Apache Tomcat
#### Đường dẫn lưu Web Server Apache Tomcat
>/opt/apache-tomcat

### 2. Cài đặt wget
```
yum install wget -y
```
### 3. Cài đặt java
```
yum install java -y
```

<a name="caidat"></a>
## II. Cài đặt
<a name="buoc1"></a>
### Bước 1: Download package dạng `*.zip`
```
wget http://mirror.downloadvn.com/apache/tomcat/tomcat-9/v9.0.6/bin/apache-tomcat-9.0.6.zip
```
<a name="buoc2"></a>
### Bước 2: Giải nén thư mục
```
unzip apache-tomcat-9.0.6.zip
```

<a name="buoc3"></a>
### Bước 3: Setup thư mục lưu trữ Apache Tomcat
- Copy thư mục vừa giải nén

```
cp -R apache-tomcat-9.0.6 /opt/
mv apache-tomcat-9.0.6/ apache-tomcat
```

<a name="buoc4"></a>
### Bước 4: Cấp quyền thực thi cho Script file
- Truy câp thư mục thực thi Tomcat

```
cd /opt/apache-tomcat/bin
```

- Cấp quyền thực thi cho Script file

```
chmod +x *.sh
```

<a name="buoc5"></a>
### Bước 5: Kiểm tra, khởi chạy dịch vụ
__Kiểm tra version Tomcat__

```
./version.sh

Using CATALINA_BASE:   /opt/apache-tomcat
Using CATALINA_HOME:   /opt/apache-tomcat
Using CATALINA_TMPDIR: /opt/apache-tomcat/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/apache-tomcat/bin/bootstrap.jar:/opt/apache-tomcat/bin/tomcat-juli.jar
Server version: Apache Tomcat/9.0.6
Server built:   Mar 5 2018 09:34:35 UTC
Server number:  9.0.6.0
OS Name:        Linux
OS Version:     3.10.0-693.2.2.el7.x86_64
Architecture:   amd64
JVM Version:    1.8.0_161-b14
JVM Vendor:     Oracle Corporation

```

__Kiểm tra cấu hình mặc định__

```
./configtest.sh

Using CATALINA_BASE:   /opt/apache-tomcat
Using CATALINA_HOME:   /opt/apache-tomcat
Using CATALINA_TMPDIR: /opt/apache-tomcat/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/apache-tomcat/bin/bootstrap.jar:/opt/apache-tomcat/bin/tomcat-juli.jar
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Server version:        Apache Tomcat/9.0.6
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Server built:          Mar 5 2018 09:34:35 UTC
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Server number:         9.0.6.0
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: OS Name:               Linux
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: OS Version:            3.10.0-693.2.2.el7.x86_64
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Architecture:          amd64
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Java Home:             /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/jre
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: JVM Version:           1.8.0_161-b14
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: JVM Vendor:            Oracle Corporation
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: CATALINA_BASE:         /opt/apache-tomcat
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: CATALINA_HOME:         /opt/apache-tomcat
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Djdk.tls.ephemeralDHKeySize=2048
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Djava.protocol.handler.pkgs=org.apache.catalina.webresources
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Dignore.endorsed.dirs=
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Dcatalina.base=/opt/apache-tomcat
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Dcatalina.home=/opt/apache-tomcat
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.VersionLoggerListener log
INFO: Command line argument: -Djava.io.tmpdir=/opt/apache-tomcat/temp
Mar 22, 2018 5:18:38 AM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: [/usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib]
Mar 22, 2018 5:18:38 AM org.apache.coyote.AbstractProtocol init
INFO: Initializing ProtocolHandler ["http-nio-8080"]
Mar 22, 2018 5:18:38 AM org.apache.tomcat.util.net.NioSelectorPool getSharedSelector
INFO: Using a shared selector for servlet write/read
Mar 22, 2018 5:18:38 AM org.apache.coyote.AbstractProtocol init
INFO: Initializing ProtocolHandler ["ajp-nio-8009"]
Mar 22, 2018 5:18:38 AM org.apache.tomcat.util.net.NioSelectorPool getSharedSelector
INFO: Using a shared selector for servlet write/read
Mar 22, 2018 5:18:38 AM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 6345 ms
```

__Chạy service Apache Tomcat__

```
./startup.sh

Using CATALINA_BASE:   /opt/apache-tomcat-test
Using CATALINA_HOME:   /opt/apache-tomcat-test
Using CATALINA_TMPDIR: /opt/apache-tomcat-test/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/apache-tomcat-test/bin/bootstrap.jar:/opt/apache-tomcat-test/bin/tomcat-juli.jar
Tomcat started.
```
__Kiểm tra service Tomcat với__

```
ps aux | grep tomcat
```

__Để tắt service Tomcat__
```
./shutdown.sh

Using CATALINA_BASE:   /opt/apache-tomcat-test
Using CATALINA_HOME:   /opt/apache-tomcat-test
Using CATALINA_TMPDIR: /opt/apache-tomcat-test/temp
Using JRE_HOME:        /usr
Using CLASSPATH:       /opt/apache-tomcat-test/bin/bootstrap.jar:/opt/apache-tomcat-test/bin/tomcat-juli.jar
```

<a name="buoc6"></a>
### Bước 6: Cấu hình base URL tomcat (docbase)
> Mặc định Tomcat sẻ dụng dụng 1 project làm trang default

> Đường dẫn project mẫu: `/opt/apache-tomcat-9.0.6/webapps/examples`

__Truy cập file cấu hình server.xml__

```
vim /opt/apache-tomcat-9.0.6/conf/server.xml
```

__Nội dung__

Trỏ đường dẫn tới project trong tomcat

```
<Context path="" docBase="/opt/apache-tomcat-9.0.6/webapps/examples">
          <!-- Default set of monitored resources -->
          <WatchedResource>WEB-INF/web.xml</WatchedResource>
</Context>
```
> Nằm trong path: `<Host name="localhost"  appBase="webapps" unpackWARs="true" autoDeploy="true"> </Host>`

__Nội dung cả file__
```
<?xml version="1.0" encoding="UTF-8"?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<!-- Note:  A "Server" is not itself a "Container", so you may not
     define subcomponents such as "Valves" at this level.
     Documentation at /docs/config/server.html
 -->
<Server port="8005" shutdown="SHUTDOWN">
  <Listener className="org.apache.catalina.startup.VersionLoggerListener" />
  <!-- Security listener. Documentation at /docs/config/listeners.html
  <Listener className="org.apache.catalina.security.SecurityListener" />
  -->
  <!--APR library loader. Documentation at /docs/apr.html -->
  <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
  <!-- Prevent memory leaks due to use of particular java/javax APIs-->
  <Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" />
  <Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" />
  <Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" />

  <!-- Global JNDI resources
       Documentation at /docs/jndi-resources-howto.html
  -->
  <GlobalNamingResources>
    <!-- Editable user database that can also be used by
         UserDatabaseRealm to authenticate users
    -->
    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />
  </GlobalNamingResources>

  <!-- A "Service" is a collection of one or more "Connectors" that share
       a single "Container" Note:  A "Service" is not itself a "Container",
       so you may not define subcomponents such as "Valves" at this level.
       Documentation at /docs/config/service.html
   -->
  <Service name="Catalina">

    <!--The connectors can use a shared executor, you can define one or more named thread pools-->
    <!--
    <Executor name="tomcatThreadPool" namePrefix="catalina-exec-"
        maxThreads="150" minSpareThreads="4"/>
    -->


    <!-- A "Connector" represents an endpoint by which requests are received
         and responses are returned. Documentation at :
         Java HTTP Connector: /docs/config/http.html
         Java AJP  Connector: /docs/config/ajp.html
         APR (HTTP/AJP) Connector: /docs/apr.html
         Define a non-SSL/TLS HTTP/1.1 Connector on port 8080
    -->
    <Connector port="80" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
    <!-- A "Connector" using the shared thread pool-->
    <!--
    <Connector executor="tomcatThreadPool"
               port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
    -->
    <!-- Define a SSL/TLS HTTP/1.1 Connector on port 8443
         This connector uses the NIO implementation. The default
         SSLImplementation will depend on the presence of the APR/native
         library and the useOpenSSL attribute of the
         AprLifecycleListener.
         Either JSSE or OpenSSL style configuration may be used regardless of
         the SSLImplementation selected. JSSE style configuration is used below.
    -->
    <!--
    <Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol"
               maxThreads="150" SSLEnabled="true">
        <SSLHostConfig>
            <Certificate certificateKeystoreFile="conf/localhost-rsa.jks"
                         type="RSA" />
        </SSLHostConfig>
    </Connector>
    -->
    <!-- Define a SSL/TLS HTTP/1.1 Connector on port 8443 with HTTP/2
         This connector uses the APR/native implementation which always uses
         OpenSSL for TLS.
         Either JSSE or OpenSSL style configuration may be used. OpenSSL style
         configuration is used below.
    -->
    <!--
    <Connector port="8443" protocol="org.apache.coyote.http11.Http11AprProtocol"
               maxThreads="150" SSLEnabled="true" >
        <UpgradeProtocol className="org.apache.coyote.http2.Http2Protocol" />
        <SSLHostConfig>
            <Certificate certificateKeyFile="conf/localhost-rsa-key.pem"
                         certificateFile="conf/localhost-rsa-cert.pem"
                         certificateChainFile="conf/localhost-rsa-chain.pem"
                         type="RSA" />
        </SSLHostConfig>
    </Connector>
    -->

    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />


    <!-- An Engine represents the entry point (within Catalina) that processes
         every request.  The Engine implementation for Tomcat stand alone
         analyzes the HTTP headers included with the request, and passes them
         on to the appropriate Host (virtual host).
         Documentation at /docs/config/engine.html -->

    <!-- You should set jvmRoute to support load-balancing via AJP ie :
    <Engine name="Catalina" defaultHost="localhost" jvmRoute="jvm1">
    -->
    <Engine name="Catalina" defaultHost="localhost">

      <!--For clustering, please take a look at documentation at:
          /docs/cluster-howto.html  (simple how to)
          /docs/config/cluster.html (reference documentation) -->
      <!--
      <Cluster className="org.apache.catalina.ha.tcp.SimpleTcpCluster"/>
      -->

      <!-- Use the LockOutRealm to prevent attempts to guess user passwords
           via a brute-force attack -->
      <Realm className="org.apache.catalina.realm.LockOutRealm">
        <!-- This Realm uses the UserDatabase configured in the global JNDI
             resources under the key "UserDatabase".  Any edits
             that are performed against this UserDatabase are immediately
             available for use by the Realm.  -->
        <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
               resourceName="UserDatabase"/>
      </Realm>

      <Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">

        <!-- SingleSignOn valve, share authentication between web applications
             Documentation at: /docs/config/valve.html -->
        <!--
        <Valve className="org.apache.catalina.authenticator.SingleSignOn" />
        -->

        <!-- Access log processes all example.
             Documentation at: /docs/config/valve.html
             Note: The pattern used is equivalent to using pattern="common" -->
        <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />
	<Context path="" docBase="/opt/apache-tomcat-9.0.6/webapps/examples">

	  <!-- Default set of monitored resources -->
	  <WatchedResource>WEB-INF/web.xml</WatchedResource>

	</Context>
      </Host>
    </Engine>
  </Service>
</Server>
```
