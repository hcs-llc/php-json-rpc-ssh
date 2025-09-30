# JSON-RPC over SSH for PHP

**Note:** This is a maintained fork of the original [datto/json-rpc-ssh](https://github.com/datto/php-json-rpc-ssh) package, which has been abandoned. This repository will be kept up-to-date with bug fixes and new features.

## Overview

This package allows you to set up a JSON-RPC client and/or server that communicates over a standard SSH connection.

This is the final piece of the JSON-RPC transport layer suite, designed to work seamlessly with the base hcs-llc/php-json-rpc package. It handles the SSH command execution and pipes the JSON-RPC messages back and forth.

For other transport layers, see the maintained forks:

* [hcs-llc/php-json-rpc](https://github.com/hcs-llc/php-json-rpc) (the base package)  
* [hcs-llc/php-json-rpc-http](https://github.com/hcs-llc/php-json-rpc-http) (for HTTP/S)

## Features

* Fully compliant with the [JSON-RPC 2.0 specifications](http://www.jsonrpc.org/specification) (with 100% unit-test coverage)
* Flexible: you can choose your own system for interpreting the JSON-RPC method strings
* Minimalistic: just two tiny files
* Ready to use, with working examples

## Examples

### Client

```php
$client = new Client($destination, $command, $options);

$client->query(1, 'add', array(1, 2));

$reply = $client->send(); // array('jsonrpc' => '2.0', 'id' => 1, 'result' => 3)
```

### Server

```php
$translator = new Translator();

$server = new Server($translator);

$server->reply();
```

*See the "examples" folder for ready-to-use examples.*

## **Requirements**

* PHP >= 7.0

## **License**

This package is released under an open-source license: [LGPL-3.0](https://www.gnu.org/licenses/lgpl-3.0.html)

## Installation

If you're using [Composer](https://getcomposer.org/), you can include this library like this:

composer require "hcs-llc/php-json-rpc-ssh"

## Getting started

1. Try the examples! Follow the README file in the "examples" directory to set up an SSH environment. Then run the examples from the project directory like this:
	```
	php examples/client.php
	```

2. Once your example is working, replace the example server code with your own code.  
3. Write a wrapper around the JSON-RPC client class that will dovetail with your project.

## Original Author

[Spencer Mortensen](http://spencermortensen.com/contact/)
