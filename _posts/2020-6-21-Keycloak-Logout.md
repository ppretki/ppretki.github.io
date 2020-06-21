---
layout: post
title: Keycloak Logout  
---

Using Keycloak Admin Console we can configure adapter's endpoint for a particular client: 

![KC Admin Endpoint](/images/kc-admin-endpoint.png)

Request sent to an adapter (path: `/k_logout`)
 
```json
{
  "id": "fc65f813-1260-49b3-8c55-6c11825c1247-1592713255576",
  "expiration": 1592713285,
  "resource": "itsense-client",
  "action": "LOGOUT",
  "notBefore": 1592713255
}
```


## Keycloak Adapter

Adapter's action handler 
[PreAuthActionsHandler.handleLogout](https://github.com/keycloak/keycloak/blob/066cdb7decd4163d28cdd9b549374a435fc47b40/adapters/oidc/adapter-core/src/main/java/org/keycloak/adapters/PreAuthActionsHandler.java#L135)

User session manager for handling logout of Spring Secured sessions
[HttpSessionManager](https://github.com/keycloak/keycloak/blob/61561968ed8dcda8c2e7521e2ed1bf746db4ad24/adapters/oidc/spring-security/src/main/java/org/keycloak/adapters/springsecurity/management/HttpSessionManager.java)
