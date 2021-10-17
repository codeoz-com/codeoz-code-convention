# Singletons

## Normally Included

The following template is for singletons for which the source code file will always be included in the project. To get the singleton instance, use following code(assuming source file has been included):
```php
myobj = Myclass:instance();
```

```php
final class Myclass {
    /** @var Myclass The one and only instance */
    public static $inst = null;

    /** Get the one and only Myclass instance */
    public static function instance(): ?Myclass {
        // Only run these methods if they haven't been ran previously
        if (null == self::$inst ) {
            self::$inst = new Myclass();
        }
        return self::$inst;   // Always return the instance
    }

    protected function __construct()  {
        static $instCount = 0;   // Count instances of this object
        HelpersPHP::die_backtrace($instCount++ > 0, 'There should only ever be a single instance of the UpdatePlugin object!');
        if(null == self::$inst) { self::$inst = $this; }  // HAVE TO set $inst in __constructor() AND instance()!
    }
}

if ( ! function_exists(__NAMESPACE__ . '\zo_Myclass')) {
    /**
     * Get the Myclass Instance
     * @return Myclass The only Myclass Instance
     */
    function zo_Myclass(): Myclass {
        if(Myclass::$inst == null) { Myclass::$inst = Myclass::instance(); }
        return Myclass::$inst;
    }
}
```

## Normally NOT Included

The following template is for singletons for which the source file will normally NOT be included in the project. This is to make the code more efficient - source file is only included when required. We can put the "zo_Myclass()" function in a "factory" file, that will includes the source code and creates the object when required. This "factory" file will always be included, be small and compact, and contain "zo_Xxx" functions for including and creating multiple singletons.

To get the singleton instance, use following code(assuming source file has been included):
```php
myobj = zo_Myclass();
```


### The Class file
```php
final class Myclass {
    /** @var Myclass The one and only instance */
    public static $inst = null;

    /** Get the one and only Myclass instance */
    public static function instance(): ?Myclass {
        // Only run these methods if they haven't been ran previously
        if (null == self::$inst ) {
            self::$inst = new Myclass();
        }
        return self::$inst;   // Always return the instance
    }

    protected function __construct()  {
        static $instCount = 0;   // Count instances of this object
        HelpersPHP::die_backtrace($instCount++ > 0, 'There should only ever be a single instance of the UpdatePlugin object!');
        if(null == self::$inst) { self::$inst = $this; }  // HAVE TO set $inst in __constructor() AND instance()!
    }
}

if ( ! function_exists(__NAMESPACE__ . '\zo_Myclass')) {
    /**
     * Get the Myclass Instance
     * @return Myclass The only Myclass Instance
     */
    function zo_Myclass(): Myclass {
        if(Myclass::$inst == null) { Myclass::$inst = Myclass::instance(); }
        return Myclass::$inst;
    }
}
```
