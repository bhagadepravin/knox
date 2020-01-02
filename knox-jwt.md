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
       <name>XASecurePDPKnox</name>
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
     <role>YARNUI</role>
     <url>http://c186-node2.squadron.support.hortonworks.com:8088</url>
   </service>

   <service>
     <role>RESOURCEMANAGER</role>
     <url>http://c186-node2.squadron.support.hortonworks.com:8088/ws</url>
   </service>
   <service>
      <role>WEBHBASE</role>
      <url>http://lhdpmstr1u.enbduat.com:60080</url>
   </service>

</topology>

```
