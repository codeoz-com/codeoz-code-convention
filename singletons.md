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

    protected function __construct()  {
        static $instCount = 0;   // Count instances of this object
        HelpersPHP::die_backtrace($instCount++ > 0, 'There should only ever be a single instance of the UpdatePlugin object!');
        if(null == self::$inst) { self::$inst = $this; }  // HAVE TO set $inst in __constructor() AND instance()!
    }
    
    /** Get the one and only Myclass instance */
    public static function instance(): ?Myclass {
        // Only run these methods if they haven't been ran previously
        if (null == self::$inst ) {
            self::$inst = new Myclass();
        }
        return self::$inst;   // Always return the instance
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

### Factory File
function zo_Myclass(?array $objArr = null): ?Myclass {
    static $do = true;  // Do first time
    if($do) {$do=false; require_once __DIR__ . '/Myclass.php'; Myclass::$inst = Myclass::instance($objArr); }
    return Myclass::$inst;
}


### The Class file
```php
namespace Codeoz\Mynamespace;
use Codeoz\Phplib1_1_dev\Core as Coz_Phplib;

defined('ABSPATH') || exit;

final class Myclass {
    /** @var Myclass The one and only instance */
    public static $inst = null;
	
    /** @var Coz_Phplib\Logger $logger The logger */
    protected $logger = null;


    /**
     * Constructor. The $objArr parameter is an array containing objects. Key is object type:
     * - logger     = A Coz_Phplib\Logger
     * @var array|null $objArr Array containing objects.
     */
    protected function __construct(?array $objArr) {
        static $instCount = 0;   // Count instances of this object
        zo_HelpersPHP()::die_backtrace($instCount++ > 0, 'There should only ever be a single instance of the Myclass object!');
        if(null == self::$inst) { self::$inst = $this; }  // HAVE TO set $inst in __constructor() AND instance()!

        if((null!=$objArr) && array_key_exists('logger', $objArr)) {
            $this->logger = $objArr['logger']??null;
        }
        if(null == $this->logger) {
            require_once 'coz_php_core_factory.php';
            $this->logger = zo_Logger();
        }
    }


    /** Get the one and only Myclass instance */
    public static function instance(?array $objArr = null): ?Myclass {
        // Only run these methods if they haven't been ran previously
        if (null == self::$inst ) {
            self::$inst = new Myclass($objArr);
        }
        return self::$inst;   // Always return the instance
    }
}
```
