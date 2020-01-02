Use to access services using oid.xml
```xml
<topology>

    <gateway>

        <provider>
            <role>federation</role>
            <name>SSOCookieProvider</name>
            <enabled>true</enabled>
            <param>
                <name>sso.authentication.provider.url</name>
                <value>https://c474-node2.squadron.support.hortonworks.com:8443/gateway/oid/api/v1/websso</value>;
            </param>
        </provider>

    </gateway>

            <service>
                <role>NAMENODE</role>
                <url>hdfs://c474-node2.squadron.support.hortonworks.com:8020</url>
            </service>

            <service>
                <role>JOBTRACKER</role>
                <url>rpc://c474-node2.squadron.support.hortonworks.com:8050</url>
            </service>

            <service>
                <role>WEBHDFS</role>
                <url>http://c474-node2.squadron.support.hortonworks.com:50070/webhdfs</url>;

            </service>

            <service>
                <role>WEBHCAT</role>
                <url>http://c474-node3.squadron.support.hortonworks.com:50111/templeton</url>;
            </service>

            <service>
                <role>OOZIE</role>
                <url>http://None:11000/oozie</url>;
            </service>

            <service>
                <role>WEBHBASE</role>
                <url>http://c474-node4.squadron.support.hortonworks.com:8080</url>;
            </service>

            <service>
                <role>HIVE</role>
                <url>http://c474-node3.squadron.support.hortonworks.com:10001/cliservice</url>;
            </service>

            <service>
                <role>RESOURCEMANAGER</role>
                <url>http://c474-node2.squadron.support.hortonworks.com:8088/ws</url>;
            </service>

            <service>
                <role>DRUID-COORDINATOR-UI</role>

            </service>

            <service>
                <role>DRUID-COORDINATOR</role>

            </service>

            <service>
                <role>DRUID-OVERLORD-UI</role>

            </service>

            <service>
                <role>DRUID-OVERLORD</role>

            </service>

            <service>
                <role>DRUID-ROUTER</role>

            </service>

            <service>
                <role>DRUID-BROKER</role>

            </service>

            <service>
                <role>ZEPPELINUI</role>
                <url>http://c474-node4.squadron.support.hortonworks.com:9995</url>;

            </service>

            <service>
                <role>ZEPPELINWS</role>
                <url>ws://c474-node4.squadron.support.hortonworks.com:9995/ws</url>

            </service>

        </topology>
```
