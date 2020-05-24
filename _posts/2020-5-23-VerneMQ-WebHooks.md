---
layout: post
title: VerneMQ Auth with Webhooks 
---

The post shows how to implement your own authentication and 
authorization extension for VerneMQ MQTT broker by using **Webhooks**.

### Docker Service 

A complete description of VerneMQ's plugin and **Webhooks** can be found [here](https://docs.vernemq.com/plugindevelopment/webhookplugins).
We can enable webhooks plugin and define some first endpoints by using the following 
`docker-compose.yml` configuration:

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=docker-compose-vernemq-webshooks.yml"></script>

It is important to note that endpoints for hooks `auth_on_register` (line 14), `auth_on_subscribe` (line 16) and `auth_on_publish` (line 18) 
need to be defined using unsecured http protocol and must point at services accessible from the docker's container.
In this simple example we can use `.env` file to define the required parameters:

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=docker-compose-vernemq-webshooks.env"></script>

### Webhooks Service

The best thing about VerneMQ's Webhhook plugin is that we can implement endpoints in any technology 
we feel comfortable with. We can use for example [sparkjava](http://sparkjava.com/):
    
<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=VerneMQWebHooks.java"></script>


### Test 

The simples way to test above setup is to use browser-based MQTT client available here 

[Online MQTT Client: (MQTT over ws)](http://www.hivemq.com/demos/websocket-client/)

Using the tool we can provide credentials and other mandatory connection's parameters

![Connect Over Web Sockets](/images/mqtt_over_ws_connect_config.png)

Operations like `connect,subscribe,publish` executed in the order produce the following logs: 

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=vernemq_webhook_endpoints.info"></script>

and leave the following trace in the broker:

<script src="https://gist.github.com/ppretki/f09499b78610c2b2b83622f560fde374.js?file=vernemq_webhook_client.trace"></script>

### Useful commands

{% highlight shell %}
vmq-admin trace client client-id=test-client
vmq-admin plugin show
vmq-admin webhooks show
vmq-admin webhooks cache show
{% endhighlight %}


### Useful links
- [VerneMQ Webhooks Plugin](https://docs.vernemq.com/plugindevelopment/webhookplugins)
