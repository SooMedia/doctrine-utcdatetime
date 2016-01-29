# Doctrine UTCDateTimeType

Doctrine2 DateTimeType that will always store your DateTime in the UTC timezone.

All the code in this library was found in [DoctrineExtensions' documentation](https://github.com/Atlantic18/DoctrineExtensions/blob/e94b30342810d028559dade3e4bac13520e93ba1/doc/timestampable.md#creating-a-utc-datetime-type-that-stores-your-datetimes-in-utc). I take no credits for this code, I just simply bundled it in a nice and easy to use package.

## Using the UTCDateTimeType

Simply copied from DoctrineExtensions' documentation:

We simply have to register and override the **datetime** type. **WARNING:** this will override the **datetime** type for all your entities and for all entities in external bundles or extensions, so if you have some entities that require the standard **datetime** type from Doctrine, you must modify the above type and use a different name (such as **utcdatetime**). Additionally, if you use DoctrineExtensions, you'll need to modify Timestampable so that it includes **utcdatetime** as a valid type.

In Symfony2 you can do this like so:

``` yaml
doctrine:
    dbal:
        types:
            datetime: SooMedia\Doctrine\DBAL\Types\UTCDateTimeType
```

In Zend Framework 2 you have to add the following to your `module.config.php`:

``` php
<?php
return array(
    // other module config here
    'doctrine' => array(
        'configuration' => array(
            'orm_default' => array( // use the name of your default configuration/connection
                'types' => array(
                    'datetime' => 'SooMedia\Doctrine\DBAL\Types\UTCDateTimeType',
                ),
            ),
        ),
        // other configuration here, like the driver config
    ),
);
```

## Credits

As I said: all credits for this piece of brilliant code goes to [DoctrineExtensions](https://github.com/Atlantic18/DoctrineExtensions/). DoctrineExtensions adds a whole bunch of extra goodies to Doctrine, so I can really recommend using it!
