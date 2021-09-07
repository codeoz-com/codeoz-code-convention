# Namespaces
Namespaces prevent class names from becoming long and avoid clashes with other classes, which could result in names such as “MyProject_Controller_FileUpload”.

By following the PHP Standards Recommendation PSR-4, the application can use Composer’s autoloading mechanism for loading files, thus decreasing complexity and adding frictionless interoperability among dependencies. 

Namespaces are defined using the keyword namespace, placed on the line immediately after the opening <?php, and can span several levels or sub-namespaces (similar to having several subdirectories where placing a file), which are separated using a \ character.

```php
namespace CoolSoft\ImageResizer\Controllers;
class ImageUpload { [...] }
```

To access the above class, we need to fully qualify its name including its namespace, and starting with a \ character. If we do NOT start with a \ character, it will be relative to the current namespace.
```php
$imageUpload = new \CoolSoft\ImageResizer\Controllers\ImageUpload();
```

Or we can also import the class into the current context, after which we can reference the class by its name directly:
```php
use CoolSoft\ImageResizer\Controllers\ImageUpload;
$imageUpload = new ImageUpload();
```
Or:
```php
use Codeoz\Phplib1_1_dev\Wp as Coz_Wplib;
$siteInfo = new Coz_Wplib\SiteInfo();
```

To access the global classes outside of namespace, start with \ character
```php
$a = new \stdClass; // Access global class, same as: $a = new stdClass;
```
