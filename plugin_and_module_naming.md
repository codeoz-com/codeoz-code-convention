
## Module Defines
Module defines for an example Module called "Template A"
```
module_name    :  Template A
module_url_lc  :  codeoz-module-template-a
```

```
MODULE_ID (lowercase) :  tmpla
MODULE_ID_UC          :  TMPLA
module_folder         :  m-tmpla      = 'm-' . MODULE_ID
module_short_name_lc  :  coz_tmpla    = 'coz_' . MODULE_ID

```

## Code Identifier prefix
Code Identifier prefix string, for **Variable**, **Function** & **Class** names, **Shortcodes**, **Options** prefix string
```
code_id_pre:  ztmpla  = 'z' . MODULE_ID
```

## Hook, Action and Filter prefix
Hooks & Wordpress Action and Filter tag prefix, used in add_action() and add_filter()
```
hook_pre:             tmpla_z_  = MODULE_ID . '_z_'
phpdoc_package_name:  cozTMPLA  = 'coz' . upper(MODULE_ID)
```
Where:
__lc = lowercase_


## HTML prefixes
The following are used for HTML 
```



## Classes & Functions
Classes & Functions declared in our Namespace do not have to be unique.
So we can easily find them, use following prefixes:
**For functions:**
```
zo_object() for functions that get objects
zh_helper() for helper functions
```


## Rename Module & Plugin
To rename module, search and rename following **files**:
```
{module_name_lc}*  to  {module_name_lc_NEW}*
{class_file_pre}*  to  {class_file_pre_NEW}*
```

To rename module, search and rename file **contents**:
```
coz_{MODULE_ID}_*        to  coz_{MODULE_ID}_*
{module_name}            to  {module_name_NEW}
{module_short_name_lc}   to  {module_short_name_lc_NEW}
{module_short_name}      to  {module_short_name_NEW}
{module_name_lc}         to {module_name_lc_NEW}
```
Replace '-' with '_' in {module_name_lc}, THEN
```
{module_name_lc}         to {module_name_lc_NEW}
```
