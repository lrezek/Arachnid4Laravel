About
=====

This is a service provider for Laravel 4.1 for the [Arachnid OGM](https://github.com/lrezek/Arachnid).

Installation
=============

Add `lrezek/arachnid4laravel` as a requirement to `composer.json`:

```JavaScript
{
    "require": {
       "lrezek/arachnid4laravel": "dev-master"
    }
}
```

You may need to add the package dependencies as well, depending on your `minimum-stability` setting:

```JavaScript
{
    "require": {
       "everyman/neo4jphp":"dev-master",
       "lrezek/arachnid":"dev-master"
    }
}
```

Update your packages with `composer update` or install with `composer install`.

Once Composer has updated your packages, you'll need to tell Lavarel about the service provider. Add the following to the `providers` in `app/config/app.php`: 

```PHP
'LRezek\Arachnid4Laravel\Providers\ArachnidServiceProvider',
```

And the facade to the `facades`:

```PHP
'Arachnid' => 'LRezek\Arachnid4Laravel\Facades\ArachnidFacade',
```

Note: You can change the name of the facade (`OGM`) to whatever you like.

Database Configuration
===========

The Neo4J database configuration is autoloaded from `app/config/database.php`. To add a Neo4J connection, simply add the following to the `connections` parameter:

```PHP
'neo4j' => array(
            'transport' => 'curl',
            'host' => 'localhost',
            'port' => '7474',
            'debug' => true,
            'proxy_dir' => '/tmp',
            'cache_prefix' => 'neo4j',
            'meta_data_cache' => 'array',
            'annotation_reader' => null,
            'username' => null,
            'password' => null,
            'pathfinder_algorithm' => null,
            'pathfinder_maxdepth' => null
        )
```

And set the default connection as follows:

```PHP
'default' => 'neo4j',
```

Usage
============================

Once this set-up is complete, you can use entities and do queries as shown in [Arachnid](https://github.com/lrezek/Arachnid). To call functions in the entity manager, simply use the facade you defined above. For example:

```PHP
Arachnid::flush()
```