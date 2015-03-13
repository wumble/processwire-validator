# Validation for ProcessWire

This module provides a set of useful validation methods.

## tl;dr ? quick example

Build configuration array:
```php
$validatorConf = array(
  'username' => array(
    'isEmpty',
    'isUnique' => array('ident' => 'name', 'sanitize' => 'username')
  ),
  'pass' => array(
    'isEmpty',
    'minLength' => array('min' => 6),
    'containsAtLeast' => array('contains' => 'digit, letter'),
    'noWhitespace'
  ),
  'email' => array(
    'isEmpty',
    'isEmail',
    'isUnique' => array('ident' => 'email', 'sanitize' => 'email')
  )
);
```

Execute validation:
```php
$validator = wire('modules')->get('Validator');
if (!$validator) throw new Wire404Exception('Validator module is not installed');
$errors = $validator->getErrors($validatorConf); // returns array
$isValid = $validator->isValid($validatorConf); // returns boolean
```

OR
```php
$validator = new Validator;
$errors = $validator->getErrors($validatorConf);
```

