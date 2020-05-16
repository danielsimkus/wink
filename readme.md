<p align="center"><img src="https://themsaid.com/img/wink.jpg"></p>

Wink adds a nice UI where you can manage a publication of any size. You can manage posts, pages, tags, and authors.

You can add photos, code blocks, featured images, social media & SEO attributes, embedded HTML (YouTube Videos, Embedded Podcasts Episodes, Tweets, ...), and markdown!

Wink is used to manage the [official Laravel blog](https://blog.laravel.com), [DivingLaravel.com](https://divinglaravel.com), and many more.  

## Installation

Wink uses a separate database connection and authentication system so that you don't have to modify any of your project code.

To install Wink, run these commands in the root of your Laravel app:

```sh
composer require themsaid/wink
php artisan wink:install
php artisan storage:link
```

**Configure the database connection** wink is going to be using in `config/wink.php`. The run:

```sh
php artisan wink:migrate
```

Head to `yourproject.test/wink` and use the provided email and password to log in.

## Updates

Add this command in your deployment script so that wink runs new migrations if any:

```sh
php artisan wink:migrate
```

You may also want to run this command to re-publish the assets:

```sh
php artisan vendor:publish --tag=wink-assets --force
```

## Uploading to S3

If you want to upload images to S3, update the `storage_disk` attribute in your `wink.php` configuration file to s3. Make sure your S3 disk is correctly configured in your `filesystems.php` configuration file.

```php
's3' => [
    'driver' => 's3',
    'key' => env('AWS_ACCESS_KEY_ID'),
    'secret' => env('AWS_SECRET_ACCESS_KEY'),
    'region' => env('AWS_DEFAULT_REGION'),
    'bucket' => env('AWS_BUCKET'),
    'url' => env('CDN_URL'),
    'options' => [
        'CacheControl' => 'public, max-age=315360000'
    ],
],
```

## Using Unsplash

Visit https://unsplash.com/oauth/applications to create a new unsplash app. Grab the 'Access Key' and add it to your `.env` file as `UNSPLASH_ACCESS_KEY`. Lastly, add unsplash to your `config/services.php` file:

```php
'unsplash' => [
    'key' => env('UNSPLASH_ACCESS_KEY'),
],
```

## Contributing

Check the [contribution guide](CONTRIBUTING.md).

## License

Wink is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
