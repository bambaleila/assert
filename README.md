php-validator
=====

[![Build Status](https://travis-ci.org/index0h/php-validator.svg)](https://travis-ci.org/index0h/php-validator) [![Dependency Status](https://gemnasium.com/index0h/php-validator.svg)](https://gemnasium.com/index0h/php-validator) [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/index0h/php-validator/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/index0h/php-validator/?branch=master) [![Code Coverage](https://scrutinizer-ci.com/g/index0h/php-validator/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/index0h/php-validator/?branch=master)

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

```sh
php composer.phar require --prefer-dist index0h/validator *
```

or add line to require section of `composer.json`

```json
"index0h/validator": *
```

## Usage

```php
use index0h\validator\Variable as v;

v::assert($var, 'var')->notEmpty()->isString()->notGraph();

// It's the same as

if (empty($var)) {
    throw new \InvalidArgumentException('Param $var must be not empty');
}

if (!is_string($var)) {
    throw new \InvalidArgumentException('Param $var must be string');
}

if (!ctype_graph($var)) {
    throw new \InvalidArgumentException('Param $var must be graph');
}
```

#### There are two ways of using `vlidator\Variable`:

* `v::assert` - It'll throw exception on first validation fail
    - mixed `$value` - checking variable
    - string `$name` - name of checking variable
    - string `$exceptionClass` (\InvalidArgumentException) - user specific exception class name
* `v::validate` - It'll check run of validations
    - mixed `$value` - checking variable
    - string `$name` - name of checking variable
    - bool `$skipOnError` (true) - by default - all validations after fail will be skiped, if false - it'll run all validations

#### Available validators

 * `isArray`
 * `notArray`

-- --
 * `isBool`
 * `notBool`

-- --
 * `isDigit`
 * `notDigit`

-- --
 * `isEmail`
 * `notEmail`

-- --
 * `isEmpty`
 * `notEmpty`

-- --
 * `isGraph`
 * `notGraph`

-- --
 * `isInt`
 * `notInt`

-- --
Both run only after `notEmpty` -> `isString`

 * `isJson`
 * `notJson`

-- --
 * `isNumeric`
 * `notNumeric`

-- --
Both run only after `notEmpty` -> `isString`

 * `isMacAddress`
 * `notMacAddress`

-- --
 * `isObject`
 * `notObject`

-- --
 * `isResource`
 * `notResource`

-- --
 * `isString`
 * `notString`


## Testing

#### Run tests from console

```sh
make test
```

#### Run benchmark from console

```sh
make benchmark
```
