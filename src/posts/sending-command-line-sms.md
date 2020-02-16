---
slug: "/sending-command-line-sms.md"
date: "2020-02-11"
title: "Sending SMS notifications via command line in PHP"
description: "How to send SMS notifications via the command line in PHP"
---

Sign up with an account at Twilio and opt for the trial account.
The trial account provides you with a set amount of funds.
You need to apply for a phone number provided by Twilio.

The app makes http POST request to Twilio and Twilio sends the SMS.

Create a project directory eg: projects/php/sms.
Use Composer to install the Twilio sdk
$projects/php/sms composer require twilio/sdk

In the project directory - $projects/php/sms - create a send-message.php file and open in text editor.

Require the Twilio helper library just obtained via composer
Declare to use the Twilio Rest client object.

Account credentials
Include the $sid and $token – find these in your Twilio account dashboard.
Place in environmental variables for extra security

$sid = $_ENV[“TWILIO_ACCOUNT_SID”];
$client = $_ENV[“TWILIO_AUTH_TOKEN”];

Use credentials to create a Twilio Rest client passing in SID and TOKEN
$client = new Client($sid, $token);

```php
<?php

require __DIR__ . '/vendor/autoload.php';
use Twilio\Rest\Client;

$sid = 'AC**********************************';
$token = 'e6********************************';
        
        $client = new Client($sid, $token);

        $client->messages->create(
            '+442323232323223',
            array(
                'from' => '+44123456789',
                'body' => 'Your text message goes here.'       
                )
            );

?>
```

Run the script which sends the message -

```
$projects/php/sms send-message.php
```

That's it for sending a basic message via the command line.