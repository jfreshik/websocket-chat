### WebSocket Chatting Application  
* SpringBoot
* WebSocket
* RabbitMQ + STOMP

### RabbitMQ + STOMP

# using STOMP plugin enabled image
* build and run test
```shell script
$ docker build -t jfreshik/rabbitmq-stomp:3 .

$ docker container run -it --name rabbitmq-stomp -p 15672:15672 -p 5672:5672 -p 61613:61613 jfreshik/rabbitmq-stomp:3
```

* docker-compose
~~~
  ...
  rabbitmq:
    image: pcloud/rabbitmq-stomp:3
    container_name: websocket-chat-queue
    ports:
      - 5672:5672
      - 15672:15672
      - 61613:61613
~~~

* Configuration(`docker/rabbitmq.config`)
    
~~~
loopback_users = none
listeners.tcp.default = 5672
default_pass = guest
default_user = guest
hipe_compile = false
management.listener.port = 15672
management.listener.ssl = false
stomp.listeners.tcp.1 = 61613
stomp.default_user = guest
stomp.default_pass = guest
~~~

* Credentials

| 구분 | id | pw |
|---|---|---|
| RabbitAdmin | guest | guest |
| STOMP | guest | guest |


### TEST

 * run application
```shell script
$ ./mvnw spring-boot:run
```

 * web chat UI
    * http://localhost:8080
