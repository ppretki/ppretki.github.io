---
layout: post
title: VerneMQ with WebHooks 
---


### Start services via `docker-compose.yml`:

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=docker_compose_vernemq_auth_redis.yml"></script>

### Configure VerneMQ auth data

{% highlight shell %}
vernemq@e17b6197beba:~$ vmq-admin webhooks cache show
+-------+------------------------------------------+----------------+-----+
| stat  |                 endpoint                 |      hook      |value|
+-------+------------------------------------------+----------------+-----+
|misses |http://192.168.1.13:10000/auth_on_register|auth_on_register|  2  |
| hits  |http://192.168.1.13:10000/auth_on_register|auth_on_register|  3  |
|entries|http://192.168.1.13:10000/auth_on_register|auth_on_register|  1  |
+-------+------------------------------------------+----------------+-----+
{% endhighlight %}



VerneMQ treats [Redis](https://redis.io/) as a simple key-value storage for both authentication 
and authorization data. Redis entries take the following form:

Key: 
{% highlight shell %}
[mountpoint, client_id, unername]
{% endhighlight %}
  
Value:
{% highlight shell %}
{
  "passhash": BCRYPT PASSWORD HASH,
  "publish_acl": [
    {
      "pattern": TOPIC PATTERN
    }
  ],
  "subscribe_acl": [
    {
      "pattern": TOPIC PATTERN
    }
  ]
}
{% endhighlight %} 

[Bcrypt](https://en.wikipedia.org/wiki/Bcrypt) password hash can be easily computed using e.g. [Online Bcrypt hash generator](https://8gwifi.org/bccrypt.jsp)
 
~~~
Brypt(pass='123',round=12) = $2a$12$uiPXR.maWj5J7Uo9mhjuMe6r.c8b1/sZtEzWV7ptkMnIomFy3l.s2
~~~   

Insert auth data into Redis:

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=set_auth_data_in_redis.sh"></script>

### Test using [Online MQTT Client: (MQTT over ws)](http://www.hivemq.com/demos/websocket-client/)

![Connect Over Web Sockets](/images/mqtt_over_ws_connect_config.png)


### Important:
- **ACL data** for a specific client are read from Redis once - during authentication (MQTT `CONNECT` command), and stay cached until the client disconnects.
- **ACL pattern** may contains template variables: %m (mountpoint), %u (username), and %c (client id) 





{% highlight shell %}
vernemq@e17b6197beba:~$ vmq-admin webhooks cache show
+-------+------------------------------------------+----------------+-----+
| stat  |                 endpoint                 |      hook      |value|
+-------+------------------------------------------+----------------+-----+
|misses |http://192.168.1.13:10000/auth_on_register|auth_on_register|  2  |
| hits  |http://192.168.1.13:10000/auth_on_register|auth_on_register|  3  |
|entries|http://192.168.1.13:10000/auth_on_register|auth_on_register|  1  |
+-------+------------------------------------------+----------------+-----+
{% endhighlight %}

### Useful commands

- show all plugins:
{% highlight shell %}
vmq-admin trace client client-id=test-client // trace mqtt client
vmq-admin plugin show // shows all plugins
vmq-admin webhooks show // show registered endpoints
vmq-admin webhooks cache show
{% endhighlight %}


### Useful tools
- [Online Bcrypt hash generator](https://8gwifi.org/bccrypt.jsp)
- [Online MQTT Client: (MQTT over ws)](http://www.hivemq.com/demos/websocket-client/)
- [Redis authentication and authorization](https://docs.vernemq.com/configuration/db-auth#redis)