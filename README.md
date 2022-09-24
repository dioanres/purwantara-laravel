# PURWANTARA LARAVEL

<h3 id="purwantara">✨ WHAT IS PURWANTARA?</h3> 
Purwantara is a digital payment service provider that helps businesses to accept digital payments with seamless and secure. Some of the payment services provided by Purwantara are Virtual Account, E Wallet, Credit Card and QRIS.

<h3 id="install">⚙️ How to install</h3>

```bash
composer require ezhasyafaat/purwantara-laravel
```

<h3 id="setup-configuration">🛠 Setup configuration</h3>

```bash
php artisan vendor:publish --provider="Ezhasyafaat\PurwantaraLaravel\PurwantaraServiceProvider" --tag="config"
```

And you have to provide bearer token in .env file. You can get bearer token at purwantara.id
```shell
PURWANTARA_TOKEN="BEARER_TOKEN_FROM_PURWANTARA"
```

<h3 id="virtual-account">💳 Virtual account</h3>
Virtual accounts is a medium for receiving payments that customer pay.

- How to create Virtual Account?
```php
use Ezhasyafaat\PurwantaraLaravel\Purwantara;
use Illuminate\Support\Str;

public function create_va()
{
    $input = [
        'display_name'      => 'John Doe', // Merchant store name
        'channel_name'      => 'BRI', //Payment channel at purwantara.id
        'order_id_merchant' => Str::uuid(), //Unique id from merchant, customize by merchant
        'expected_amount'   => 10000, //Amount of virtual account
        'description'       => 'Testing create virtual account' //Description of virtual account
    ];

    $response = Purwantara::create_virtual_account($input);
}
```