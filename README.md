## PHP Helper Functions extracted from Laravel

This project has extracted useful [helper functions from laravel framework](http://laravel.com/docs/5.6/helpers), which can be used outside Laravel.

## Installation

You can install the package via composer:

```bash
composer require hkp22/php-helpers
```

## Usage

* **[Arrays](#arrays)**
  * [array_add()](#array_add)
  * [array_get()](#array_get)
  * [array_set()](#array_set)
* **[Miscellaneous](#miscellaneous)**
  * [dd()](#dd)
  * [value()](#value)


## Arrays
<a name="arrays"></a>


### `array_add()`
<a name="array_add"></a>

The `array_add` function adds a given key/value pair to an array if the given key doesn't already exist in the array:

```php
$array = array_add(['name' => 'Desk'], 'price', 100);

// ['name' => 'Desk', 'price' => 100]
```

### `array_get()`
<a name="array_get"></a>

The `array_get` function retrieves a value from a deeply nested array using "dot" notation:

```php
$array = ['products' => ['desk' => ['price' => 100]]];

$price = array_get($array, 'products.desk.price');

// 100
```

### `array_set()`
<a name="array_set"></a>

The `array_set` function sets a value within a deeply nested array using "dot" notation:

```php
$array = ['products' => ['desk' => ['price' => 100]]];

array_set($array, 'products.desk.price', 200);

// ['products' => ['desk' => ['price' => 200]]]
```

## Miscellaneous
<a name="miscellaneous"></a>


### `dd()`
<a name="dd"></a>

The `dd` function dumps the given variables and ends execution of the script:

```php
dd($value);

dd($value1, $value2, $value3, ...);
```

### `value()`
<a name="value"></a>

The `value` function returns the value it is given. However, if you pass a Closure to the function, the Closure will be executed then its result will be returned:

```php
$result = value(true);

// true

$result = value(function () {
    return false;
});

// false
```
