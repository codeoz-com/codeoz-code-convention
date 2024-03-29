
**IMPORTANT** - This documentation moved to 'docs' folder in 'codeoz/php-lib' repository

## Defines
Plugin/Module defines, following examples are for a **Plugin** called "Multistore and Inventory", and **Module** called "Template A"
```
plugin_name       :  multistore-and-inventory
plugin_desc       :  CodeOz Multistore and Inventory
plugin_desc_short :  Multistore and Inventory

module_name       :  Template A
module_name_us    :  Template_A
module_name_us_lc :  template_a
module_url        :  codeoz-module-template-a
```

```
module_id (lowercase) :  tmpla
module_id_uc          :  TMPLA
module_folder         :  m-tmpla      = 'm-' . module_id
module_short_name_lc  :  coz_tmpla    = 'coz_' . module_id
cvs_version           :  TMPLA_0_dev
```
## Codeoz Prefix
Codeoz Prefix, with trailing underscore, for **WP Domain**.  
For example: coz_ppas_
```
id_pre: coz_tmpla  = 'coz_' . module_id . '_'
```

## Code Identifier prefix
Code Identifier prefix string, for **Variable**, **Function** & **Class** names, **Shortcodes**, **Options** prefix string.  
For example: ztmpla
```
code_id_pre:  ztmpla  = 'z' . MODULE_ID
```

## Hook, Action and Filter prefix
**Hooks** & Wordpress **Action** and **Filter** tag prefix, used in add_action() and add_filter().  
For example: tmpla_z_
```
hook_pre:             tmpla_z_  = MODULE_ID . '_z_'
phpdoc_package_name:  cozTMPLA  = 'coz' . upper(MODULE_ID)
```

## HTML prefixes

### HTML Fields
If HTML Fields have the following prefixes, they will be processed by the CodeOz "POST Processor".
- The 'XX' part is the "**Data Type**", and indicates where the field should be saved(Options, Properties...).
- The "**Field ID**" is used to build a unique field name used for options or other. Can also be an **array** by adding "\[element\]" to it.

**Field Types:**
```
czfcb_XX_{field ID}   : Check Box
czfcbm_XX_{field ID}  : Check Box Multi
czfclr_XX_{field ID}  : Color
czfimg_XX_{field ID}  : Image
czfnr_XX_{field ID}   : Number
czfpw_XX_{field ID}   : Passord
czfr_XX_{field ID}    : Radio Button
czfs_XX_{field ID}    : Select
czfsm_XX_{field ID}   : Select Multi
czft_XX_{field ID}    : Text input
czfts_XX_{field ID}   : Text sectet
czfta_XX_{field ID}   : Text Area input
codeoz-ajax           : AJAX request
```

**Data Type**
Following Data Types are currently defined:
```
o  : Save to Options. Will prefix 'z{ID}_' to the 'Field ID' to get the option name to save to.
```

**Field Type**
This is the name used to store the option. It can be a single value, or an array(example zmulinv_grid\[text_size\])

**AJAX**
Is there is a POST variable name 'codeoz-ajax', it is handled by AJAX callback

**Examples 1**
For example, the following string is for a 'Radio Button', and it's value should be saved to the Option with name 'zppas_my_option'. The part of the name up until
the first '_' character is the Plugin/Module 'Code ID Prefix'. For this example the field was called for a Plugin/Module with ID 'ppas'
```
czfr_o_zppas_my_option
```
**Examples 2**
For example, the following string is for a 'Text Input', and it's value should be saved to the Option Array with name 'zppas_grid\[text_size\]'. The part of the name up until
the first '_' character is the Plugin/Module 'Code ID Prefix'. For this example the field was called for a Plugin/Module with ID 'ppas'
```
czft_o_zppas_grid[text_size]
```


### POST Parameter
The following are used for HTML POST Parameter
```
coz_proc_name :    The 'POST Processor' name, is same as Classname and filename(wihout '.php') of file containing it
coz_proc_ns   :    The 'POST Processor' namespace, WITHOUT trailing backslash. Or empty string if none.
coz_proc_path :    The 'POST Processor' path, relative to 'plugins' path, and WITHOUT trailing slash
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
No files have to be renames
```

To rename module, search and rename file **contents**:
```
namespace Codeoz\{cvs_version_OLD);     to    namespace Codeoz\{cvs_version};

'z{MODULE_ID_old}_*                     to    'z{MODULE_ID}_*
"z{MODULE_ID_old}_*                     to    "z{MODULE_ID}_*
z{MODULE_ID_old}_*                      to    z{MODULE_ID}_*
z{MODULE_ID_old}*                       to     z{MODULE_ID}*

coz_{MODULE_ID_old}*                    to    coz_{MODULE_ID}*
coz-{MODULE_ID_old}*                    to    coz-{MODULE_ID}*

'{MODULE_ID_old}'                       to    '{MODULE_ID}'
"{MODULE_ID_old}"                       to    "{MODULE_ID}"

'{MODULE_ID_uc_OLD}'                    to    '{MODULE_ID_uc}'
"{MODULE_ID_uc_OLD}"                    to    "{MODULE_ID_uc}"

{cvs_version_OLD}                       to    {cvs_version}
```
