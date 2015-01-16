# Meck Wrapper for RabbitMQ

Meck is a pretty awesome mock library for erlang, we want to use it in
our RabbitMQ plugins. This repository is just the bridge to the
RabbitMQ build system.

## How to use this wrapper

This is usually the layout of a development environment for RabbitMQ
plugins that supports this wrapper:

```
  rabbitmq-public-umbrella
    |
    - rabbitmq-*
    - your-rabbitmq-plugin
    - meck-wrapper <-- Here's our guy!
```

After that, change the `package.mk` file inside of your plugin and add
`meck-wrapper` to the `DEPS` var. Here's an example of a `package.mk`
file that uses meck:

```
PACKAGE_NAME:=rabbit_presence_exchange
APP_NAME:=rabbit_presence_exchange
DEPS:=rabbitmq-erlang-client meck-wrapper
STANDALONE_TEST_COMMANDS:=presence_exchange_test:all_tests()
```
