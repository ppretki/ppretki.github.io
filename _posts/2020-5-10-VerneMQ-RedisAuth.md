---
layout: post
title: VerneMQ with Redis Auth 
---

Information found on this page allows you to quickly configure MQTT VerneMQ broker
so that it uses [Redis](https://redis.io/) as a data source during authentication and authorization 
processes.    

## Docker Services

The simples way to make the VerneMQ and Redis work together is to define the services 
in a docker-compose file: 

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=docker-compose-vernemq-auth-redis.yml"></script>

### VerneMQ Auth Data

When the broker receives `CONNECT` command from external clients it tries to authenticate them 
on the basis of data available in Redis. VerneMQ assume following structure for the authentication data:   


* Redis Key

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=auth_data_redis_key_pattern.data"></script>

* Redis Value

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=auth_data_redis_value_pattern.data"></script>


where:

* `mountpoint`, `client id`, `username` - credentials  

* `passhas` - Bcrypted authentication password,

[Bcrypt](https://en.wikipedia.org/wiki/Bcrypt) password hash can be easily computed using e.g. [Online Bcrypt hash generator](https://8gwifi.org/bccrypt.jsp) 
~~~
Brypt(pass='123',round=12) = $2a$12$uiPXR.maWj5J7Uo9mhjuMe6r.c8b1/sZtEzWV7ptkMnIomFy3l.s2
~~~   

* `Publish ACL`, `Subscribe ACL` - complete description can found at [VerneMQ](https://docs.vernemq.com/configuration/db-auth)

### Insert Auth Data into Redis

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=set_auth_data_in_redis.sh"></script>

### Test using [Online MQTT Client: (MQTT over ws)](http://www.hivemq.com/demos/websocket-client/)

![Connect Over Web Sockets](/images/mqtt_over_ws_connect_config.png)


### Important:
- **ACL data** for a specific client are read from Redis once - during authentication (MQTT `CONNECT` command), and stay cached until the client disconnects.
- **ACL pattern** may contains template variables: %m (mountpoint), %u (username), and %c (client id) 


### Useful commands

{% highlight shell %}
vmq-admin trace client client-id=test-client
vmq-admin plugin show
vmq-admin webhooks show
vmq-admin webhooks cache show
{% endhighlight %}


### Useful tools
- [Online Bcrypt hash generator](https://8gwifi.org/bccrypt.jsp)
- [Online MQTT Client: (MQTT over ws)](http://www.hivemq.com/demos/websocket-client/)
- [Redis authentication and authorization](https://docs.vernemq.com/configuration/db-auth#redis)
