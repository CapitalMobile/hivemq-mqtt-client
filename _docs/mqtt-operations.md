---
nav_order: 5
redirect_from: /docs/mqtt_operations.html
---

# MQTT Operations

Most MQTT operations provide a fluent builder API or can be called with a prebuilt MQTT message.

{% capture tab_content %}

Fluent
===

```java
client.publishWith()
        .topic("test/topic")
        .qos(MqttQos.AT_LEAST_ONCE)
        .payload("payload".getBytes())
        .send();
```

====

Prebuilt message
===

```java
Mqtt5Publish publishMessage = Mqtt5Publish.builder()
        .topic("test/topic")
        .qos(MqttQos.AT_LEAST_ONCE)
        .payload("payload".getBytes())
        .build();

client.publish(publishMessage);
```

{% endcapture %}
{% include tabs.html group="mqtt-operation-style" content=tab_content %}

Some MQTT operations also provide methods without any arguments if no mandatory fields have to be set.
Then the default parameters (as defined in the MQTT specification or reasonable defaults if not defined there) will be 
used.

```java
client.connect();
client.disconnect();
```

All MQTT operations are safe to be called by different threads.