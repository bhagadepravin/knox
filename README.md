# knox


cdp-dc knox kerberos topology using CM
```bash
Goto -> CM -> Knox -> Knox Gateway Advanced Configuration Snippet (Safety Valve) for conf/cdp-resources.xml


name = providerConfigs:kerberos1
value = role=authentication#authentication.name=HadoopAuth#authentication.param.config.prefix=hadoop.auth.config#authentication.param.hadoop.auth.config.signature.secret=knox-signature-secret#authentication.param.hadoop.auth.config.type=kerberos#authentication.param.hadoop.auth.config.simple.anonymous.allowed=false#authentication.param.hadoop.auth.config.token.validity=1800#authentication.param.hadoop.auth.config.cookie.domain=root.hwx.site#authentication.param.hadoop.auth.config.cookie.path=/gateway/kerberos1#authentication.param.hadoop.auth.config.kerberos.principal=HTTP/knox-workshop-1.knox-workshop.root.hwx.site@ROOT.HWX.SITE#authentication.param.hadoop.auth.config.kerberos.keytab=/home/knox.keytab#authentication.param.hadoop.auth.config.kerberos.name.rules=DEFAULT#role=identity-assertion#identity-assertion.name=Default#role=authorization#authorization.name=XASecurePDPKnox



name = kerberos1
value = providerConfigRef=kerberos#discoveryType=ClouderaManager#discoveryAddress=https://knox-workshop-1.knox-workshop.root.hwx.site:7183/#cluster=Cluster 1#discoveryUser=admin#discoveryPasswordAlias=admin#WEBHDFS
```
