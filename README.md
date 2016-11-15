# Confluence PHP Client
A Confluence RESTful API client in PHP

An Object Oriented wrapper for Confluence, written PHP5

## Requirements

* PHP >= 5.5.0

## Installation

```bash
$ php composer.phar require rainflute/confluence-php-client
```

## Usage

```php
<?php

use Rainflute/ConfluenceClient/Client;
use Rainflute/ConfluenceClient/Curl;
use Rainflute/ConfluenceClient/Entity/ConfluencePage;

//Create and configure a curl web client
$curl = new Curl('confluence_host_url,'username','password');

//Create the Confluence Client
$client = new Client($curl);

//Create a confluence page
$page = new ConfluencePage();

//Configure your page
$page->setSpace('testSpaceKey')->setTitle('Test')->setContent('<p>test page</p>');

//Create the page in confluence in the test space
$client->createPage($page);

//Get the page we created
echo $client->selectPageBy([
    'spaceKey' => 'testSpaceKey',
    'title' => 'Test'
]);

```


### Get your development instance

Atlassian changed the way to work on Confluence/Jira, now in order to create your plugin, you have to get a [Developer Account](http://go.atlassian.com/cloud-dev) and create your own instance. All the steps to create your environment are defined on the [documentation page](https://developer.atlassian.com/static/connect/docs/latest/guides/development-setup.html).

Once you have access to your own Atlassian Cloud instance and you put it in developer mode, we can continue and let the instance contact us.

