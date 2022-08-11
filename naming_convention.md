
**IMPORTANT** - This documentation moved to root 'docs' folder in 'codeoz/php-lib'

## Functions, Variable and Action/Filter names
Use lowercase letters in **variable, action/filter**, and **function names**(never camelCase). Separate words via underscores. Don’t abbreviate variable names unnecessarily; let the code be unambiguous and self-documenting.
```php
function some_name( $some_variable ) { [...] }
```

## Class names and filenames
**Class names** should use capitalized words separated by underscores OR camelCase
Any **acronyms** should be all upper case.
When using **namespaces**, class names do NOT need to be preceded by an identifier, like “COZ_” for example.
```php
class Logger { [...] }       ==> in “Logger.php”

class SiteDefs { [...] }     ==> in “SiteDefs.php”

class Site_Stats { [...] }   ==> in “Site-Stats.php”

--- OR CamelCase ---

class CozActnPrty { [...] }   ==> in “COZ-Actn-Prty.php”
```

**Class file** names should be “Classname.php”(Start with **Uppercase**) with **underscores** replaced with **hyphens**, for example
```
Site_Defs class in Site-Defs.php
```

## Constants
Constants should be in all upper-case with underscores separating words:
```php
define( 'DOING_AJAX', true );
define( 'DOING_AJAX', true );
```

## File Names

Files should be named:
- Descriptively
- All **lowercase** for files NOT containing classes
- Start with uppercase for files containing classes, with hyphens separating words
- **Hyphens** should separate words

For example:
```php
my-plugin-name.php
My-Class.php
```

Files containing **template** tags in wp-includes should have -template appended to the end of the name so that they are obvious. For example:
```php 
general-template.php
```
