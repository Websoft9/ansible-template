# Parameters

The RabbitMQ deployment package contains a sequence software (referred to as "components") required for RabbitMQ to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

## Path

### RabbitMQ

RabbitMQ installation directory:  */data/rabbitmq*  
RabbitMQ logs directory:  */data/logs/rabbitmq*  

### Erlang

Erlang installation directory:  */data/erlang*  

## Ports

You can control(open or shut down) ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** of your Cloud Server whether the port can be accessed from Internet.

You can run the cmd `netstat -tunlp` to list all used ports, and we list the following most useful ports for you:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| HTTP | 8161 | HTTP requests for RabbitMQ Console| Required |
| HTTPS | 5672 | epmd | Optional |
| TCP | 55672 | Erlang distribution | Optional |


## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Check all components version
sudo cat /data/logs/install_version.txt

# Linux Version
lsb_release -a

# erlang  Version
yum info erlang
apt show erlang

# RabbitMQ version
rabbitmqctl status | grep RabbitMQ*
```