#cracklib_php
**Author: Alexandru Mos**

CrackLib PHP is made to provide a quick interface for the cracklib-check binary. Checks if a password is good enought to use it. Includes a helper for Code Igniter.

### Usage

How to use it:
```php
<?php

    require_once 'cracklib.php';

    $check_result = cracklib_check('some_password');

    var_dump($check_result);

?>
```

This example will output:
```
array(3) {
  ["good_password"]=>
  int(1)
  ["status_code"]=>
  int(1)
  ["cracklib_msg"]=>
  string(2) "OK"
}
```

The cracklib_check function always returns an asociative array containing:
* good_password (int): 1 if the password is safe enough and can be used, 0 otherwise;
* status_code (int): 1 if the password can be used, 10 to 15 to signal various statuses (explained under);
* cracklib_msg (string): ok if the password can be used, otherwise explains the problem with the password;

### Status codes

Here are all the status codes explained:
* 1: the password is ok and can be used;
* 10: it does not contain enough different characters;
* 11: it is very short;
* 12: it is too short;
* 13: it is too simple;
* 14: it is based on a dictionary word;
* 15: unknown problem with the password.