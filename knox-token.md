# Knox Token

1.  Create one topology  file as shown in the attached file jwt.xml and make sure the permission is set to knox:knox

```xml
<topology>

   <gateway>
     <provider>
      <role>identity-assertion</role>
      <name>Default</name>
      <enabled>true</enabled>
     </provider>

     <provider>
       <role>authorization</role>
       <name>AclsAuthz</name>
       <enabled>true</enabled>
     </provider>

     <provider>
       <role>federation</role>
       <name>JWTProvider</name>
       <enabled>true</enabled>
      <param>
       <!-- knox.token.audiences is optional -->
       <name>knox.token.audiences</name>
       <value>tokenbased</value>
      </param>
     </provider>
   </gateway>

   <!-- Add Hadoop Services allowed jwt access, here use Yarn UI as an example -->
            <service>
                <role>WEBHDFS</role>
                <url>http://c174-node2.squadron.support.hortonworks.com:50070/webhdfs</url>
<url>http://c174-node3.squadron.support.hortonworks.com:50070/webhdfs</url>

            </service>
        </topology>
```


2. Create knoxsso-jwt.xml
  
```xml
            <topology>
            <gateway>
            <provider>
            <role>webappsec</role>
            <name>WebAppSec</name>
            <enabled>true</enabled>
            <param><name>xframe.options.enabled</name><value>true</value></param>
            </provider>

            <provider>
            <role>authentication</role>
            <name>ShiroProvider</name>
            <enabled>true</enabled>
            <param>
            <name>sessionTimeout</name>
            <value>30</value>
            </param>
            <param>
            <name>redirectToUrl</name>
            <value>/gateway/knoxsso/knoxauth/login.html</value>
            </param>
            <param>
            <name>restrictedCookies</name>
            <value>rememberme,WWW-Authenticate</value>
            </param>
            <param>
            <name>main.ldapRealm</name>
            <value>org.apache.hadoop.gateway.shirorealm.KnoxLdapRealm</value>
            </param>
            <param>
            <name>main.ldapContextFactory</name>
            <value>org.apache.hadoop.gateway.shirorealm.KnoxLdapContextFactory</value>
            </param>
            <param>
            <name>main.ldapRealm.contextFactory</name>
            <value>$ldapContextFactory</value>
            </param>
            <param>
            <name>main.ldapRealm.userDnTemplate</name>
            <value>uid={0},ou=people,dc=hadoop,dc=apache,dc=org</value>
            </param>
            <param>
            <name>main.ldapRealm.contextFactory.url</name>
            <value>ldap://localhost:33389</value>
            </param>
            <param>
            <name>main.ldapRealm.authenticationCachingEnabled</name>
            <value>false</value>
            </param>
            <param>
            <name>main.ldapRealm.contextFactory.authenticationMechanism</name>
            <value>simple</value>
            </param>
            <param>
            <name>urls./**</name>
            <value>authcBasic</value>
            </param>
            </provider>

            <provider>
            <role>identity-assertion</role>
            <name>Default</name>
            <enabled>true</enabled>
            </provider>
            </gateway>

            <application>
            <name>knoxauth</name>
            </application>

            <service>
   <!--         <role>KNOXSSO</role>
                            <param>
            <name>knoxsso.cookie.secure.only</name>
            <value>false</value>
            </param>
            <param>
            <name>knoxsso.token.ttl</name>
            <value>30000</value>
            </param> -->
   <role>KNOXTOKEN</role>
   <param>
      <name>knox.token.ttl</name>
      <value>600000</value>
   </param>
   <!-- knox.token.audiences is optional, must meet what's configured in JWTProvider -->
   <param>
      <name>knox.token.audiences</name>
      <value>tokenbased</value>
   </param>
   <param>
      <name>knox.token.target.url</name>
      <value>https://c174-node3.squadron.support.hortonworks.com:8443/gateway/tokenbased</value>
   </param>
            </service>

            </topology>
```
3.  Use the below url to generate Jwt token

 `curl -ivku <username>:<password> https://{KNOX_HOST}:8443/gateway/knoxsso-jwt/knoxtoken/api/v1/token`

4. Use the generated token to access service through knox as shown below

 `curl -ivk -H "Authorization: Bearer <token string>" https://<knox host>:8443/gateway/<topology name>/<service>`

Ex:  `url -ivk -H "Authorization: Bearer <token string>" https://<knox host>:8443/gateway/jwt/webhdfs/v1/tmp?op=LISTSTATUS`
