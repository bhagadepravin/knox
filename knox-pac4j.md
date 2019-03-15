# knox-pac4j

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
                  <role>federation</role>
                  <name>pac4j</name>
                  <enabled>true</enabled>
                  <param>
                    <name>pac4j.callbackUrl</name>
                    <value>https://c174-node3.squadron-labs.com:8443/gateway/knoxsso/api/v1/websso</value>
                  </param>
                  <param>
                    <name>clientName</name>
                    <value>OidcClient</value>
                  </param>
                  <param>
                    <name>oidc.id</name>
                    <value>mQszAwbaxJvfW46XNp4bSobAbhxuJe8j</value>
                  </param>
                  <param>
                    <name>oidc.secret</name>
                    <value>gx0TnHpbN1-1Kb13c1L5GCxcNvQt70A7278L3pzljpXEcUKH9Jfwvj8R3pgVdsfY</value>
                  </param>
                  <param>
                    <name>oidc.discoveryUri</name>
                    <value>https://pravinknoxtest.auth0.com/.well-known/openid-configuration</value>
                  </param>
                  <param>
                    <name>oidc.preferredJwsAlgorithm</name>
                    <value>RS256</value>
                  </param>
              </provider>
          </gateway>
          <application>
            <name>knoxauth</name>
          </application>
          <service>
              <role>KNOXSSO</role>
              <param>
                  <name>knoxsso.cookie.secure.only</name>
                  <value>false</value>
              </param>
              <param>
                  <name>knoxsso.token.ttl</name>
                  <value>3600000</value>
              </param>
       <param>
         <name>knoxsso.redirect.whitelist.regex</name>
         <value>^/.*$;^https?://(.+\.squadron-labs\.com|):[0-9]+/?.*$</value>
      </param>>
          </service>
      </topology>
      ```

Ref: https://community.hortonworks.com/articles/171892/configure-knox-with-openid-connect.html
Ref: https://knox.apache.org/books/knox-0-12-0/user-guide.html#Pac4j+Provider+-+CAS+/+OAuth+/+SAML+/+OpenID+Connect
Ref: https://knox.apache.org/books/knox-0-12-0/user-guide.html#For+OpenID+Connect+support:
