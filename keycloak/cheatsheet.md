```bash
Knox- OAuth Protocol configuration

yum install java -y
wget https://downloads.jboss.org/keycloak/7.0.1/keycloak-7.0.1.tar.gz
tar -xvzf keycloak-7.0.1.tar.gz
mv keycloak-7.0.1 keycloak
cd keycloak/bin/
./standalone.sh

http://172.25.39.143:9990

http://172.25.39.143:9990/management
http://localhost:8080/auth/admin/



http://172.25.35.18:9990


http://172.25.35.18:9990



sudo -u keycloak ./bin/add-user-keycloak.sh --user admin --password a2b42bef11d5646c5e0af8792c5461e1f1e61981 --realm master


[root@c374-node3 keycloak]# ./bin/add-user-keycloak.sh --user admin --password a2b42bef11d5646c5e0af8792c5461e1f1e61981 --realm master
Added 'admin' to '/root/knox/keycloak/standalone/configuration/keycloak-add-user.json', restart server to load user

./bin/add-user-keycloak.sh --user pravin --password Welcome  --realm master
Added 'pravin' to '/root/knox/keycloak/standalone/configuration/keycloak-add-user.json', restart server to load user
[root@c374-node3 keycloak]#


sudo -u keycloak ./bin/jboss-cli.sh 'embed-server,/subsystem=undertow/server=default-server/http-listener=default:write-attribute(name=proxy-address-forwarding,value=true)'
sudo -u keycloak ./bin/jboss-cli.sh 'embed-server,/socket-binding-group=standard-sockets/socket-binding=proxy-https:add(port=8443)'
sudo -u keycloak ./bin/jboss-cli.sh 'embed-server,/subsystem=undertow/server=default-server/http-listener=default:write-attribute(name=redirect-socket,value=proxy-https)'
Or you can use a



I have deleted my environment but , I have key cloak setup in open stack instance. Which you can use. 

172.26.88.231 	raghav-infra.raghav.com raghav-infra.squadron.support.hortonworks.com


You can access key cloak UI https://172.26.88.231:8443/auth/


It is a standalone setup where you can add users after creating the client 

Login to admin console using admin/tender12. Create new client to use with your env. It is a standalone setup where you can add users after creating the client and setup Knox SSO following the steps in GitHub. 


http://172.26.88.231:8080/auth/realms/master/protocol/saml


http://172.26.88.231:8080/auth/realms/raghav/protocol/saml


https://raghav-infra.raghav.com:18443/gateway/keycloak/api/v1/websso


curl -ik https://raghav-infra.raghav.com:8443/auth/realms/protocol/saml/descriptor -o idp.xml

curl -ik http://172.26.88.239:8080/auth/realms/master/protocol/saml/descriptor -o idp.xml


++++++++++++++++


http://172.26.88.239:8080/auth/realms/master/protocol/saml/descriptor


curl -ik http://172.26.88.239:8080/auth/realms/master/protocol/saml/descriptor

# keytool -import -file /tmp/knoxcert.crt -keystore $JAVA_HOME/jre/lib/security/cacerts -alias AD-Cert -storepass changeit










```
