# ActiveMQ Container Usage

Configure using the following environment variables:

| Variable | Description | Values |
|----------|-------------|--------|
|ACTIVEMQ_JMX_ENABLED|Should enable context manager|`true`,`false`|
|ACTIVEMQ_LIMITS_MEMORY|Memory usage as explained [here](https://activemq.apache.org/producer-flow-control.html)|ex: `100 mb`|
|ACTIVEMQ_LIMITS_STORE|Store usage as explained [here](https://activemq.apache.org/producer-flow-control.html)|ex: `100 gb`|
|ACTIVEMQ_LIMITS_TMP|Temp usage as explained [here](https://activemq.apache.org/producer-flow-control.html)|ex: `1 gb`|
|ACTIVEMQ_TCP|OpenWire Port|ex: `61616`|
|ACTIVEMQ_AMQP|AMQP Port|ex: `5672`|
|ACTIVEMQ_STOMP|STOMP Port|ex: `61613`|
|ACTIVEMQ_MQTT|MQTT Port|ex: `1883`|
|ACTIVEMQ_WS|WS Port|ex: `61614`|
|ACTIVEMQ_CREDENTIALS_FILE|Credentials filename (relative to `${activemq.conf}` which use to be `/opt/activemq/conf`)|ex: `credentials.properties`|
|ACTIVEMQ_BROKER_NAME|Broker name|ex: `localhost`|
|ACTIVEMQ_USERS_ADMIN_ROLE|Admin role|ex: `admin`|
|ACTIVEMQ_USERS_ADMIN_PASSWORD|Admin UI password|ex: `admin`|
|ACTIVEMQ_USERS_xxxxx_ROLE|`xxxxx` UI user role|ex: `guest`|
|ACTIVEMQ_USERS_xxxxx_PASSWORD|`xxxxx` UI user password|ex: `guest`|


# Sample compose file

Sample for use with docker-compose

```yaml
version: '3.6'
services:
  mq:
    image: jairov4/activemq:5.14.5-alpine
    environment:
      ACTIVEMQ_USERS_ADMIN_ROLE: the_admin
      ACTIVEMQ_USERS_ADMIN_PASSWORD: the_password
    ports:
      - 8161:8161
    volumes:
      - mq_data:/opt/activemq/data

volumes:
  mq_data:
```

