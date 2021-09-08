
```
module_text_name :        Codeoz Module Template A
module_name_lc :          module_teplate_a
main class :              Module_Template_A
module_url_lc :           codeoz-module-template-a
module_id (lowercase) :   tmpla
module_folder :           m-tmpla      = 'm-' . $module_id
module_short_name_lc :    coz_tmpla    = 'coz_' . $module_id
singleton_class_name :    Codeoz_TMPLA = 'Codeoz_' . upper($module_id)
```

## Code Identifier prefix string, for variable, function, class names, shortcodes, options
```
code_id_pre:  ztmpla  = 'z' . $module_id
```

## Codeoz Identifier prefix string
```
coz_id_pre:  coz_tmpla_  = 'z' . $module_id . '_'
```

## Hooks & Wordpress Action and Filter tag prefix, used in add_action() and add_filter()
```
hook_pre:             tmpla_z_  = $module_id . '_z_'
phpdoc_package_name:  cozTMPLA  = 'coz' . upper($module_id)
```
Where:
__lc = lowercase_


## Functions
Functions declared in our Namespace do not have to be unique. So we can easily find them, use following prefixes
```
zo_object() for functions that get objects
zh_helper() for helper functions
```
To rename module, search and replace following:


## Filename
```
{module_name_lc}*  to  {module_name_lc_NEW}*
{class_file_pre}*  to  {class_file_pre_NEW}*
```


## File Content
```
coz_{abbrv_lowercase}_*     to  coz_{abbrv_lowercase_NEW}_*
{module_name}               to  {module_name_NEW}
{module_short_name_lc}      to  {module_short_name_lc_NEW}
{module_short_name}         to  {module_short_name_NEW}
{module_name_lc}            to {module_name_lc_NEW}
```
Replace '-' with '_' in {module_name_lc}, THEN
```
{module_name_lc}            to {module_name_lc_NEW}
```
