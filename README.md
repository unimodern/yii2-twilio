Twilio for Yii2
================
This component is YII2 wrapper for Twilio PHP SDK.

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist filipajdacic/yii2-twilio "*"
```

or add

```
"filipajdacic/yii2-twilio": "*"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it in your code by putting this in your config:
```php
'components' => array(
    ...
    'Yii2Twilio' => array(
        'class' => 'filipajdacic\yiitwilio\YiiTwilio',
        'account_sid' => 'YOUR_TWILIO_ACCOUNT_SID_HERE',
        'auth_key' => 'YOUR_TWILIO_AUTH_KEY_HERE', 
    ),
    ...
);
```

After you have configured a component, you can use it for example in this way:

```php

    $twilioService = Yii::$app->Yii2Twilio->initTwilio();

    try {
        $message = $twilioService->account->messages->create(array(
            "From" => "+12345678901", // From a valid Twilio number
            "To" => "+12345678901",   // Text this number
            "Body" => "Hello from my Yii2 Application!",
        ));
    } catch (\Services_Twilio_RestException $e) {
            echo $e->getMessage();
    }

```

For mor SDK functions and usage documentation feel free to visit official Twilio PHP SDK documentation section [here](https://www.twilio.com/docs/libraries/php).

If you have any questions, feel free to ask.