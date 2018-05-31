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
  * [array_build()](#array_build)
  * [array_divide()](#array_divide)
  * [array_dot()](#array_dot)
  * [array_except()](#array_except)
  * [array_first()](#array_first)
  * [array_last()](#array_last)
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

### `array_build()`
<a name="array_build"></a>

Build a new array using a callback.

```php
$array = [
    'us' => 'united states',
    'uk' => 'united kingdom',
    'in' => 'india',
  ];

// run array_build function
$result = array_build($array, function ($key, $value) {
    return [strtoupper($key), ucwords($value)];
});

// Output
// ['US' => 'United States', 'UK' => 'United Kingdom', 'IN' => 'India']

```

### `array_divide()`
<a name="array_divide"></a>

The `array_divide` function returns two arrays, one containing the keys, and the other containing the values of the given array:

```php
[$keys, $values] = array_divide(['name' => 'Desk']);

// $keys: ['name']

// $values: ['Desk']
```

### `array_dot()`
<a name="array_dot"></a>

The `array_dot` function flattens a multi-dimensional array into a single level array that uses "dot" notation to indicate depth:

```php
$array = ['products' => ['desk' => ['price' => 100]]];

$flattened = array_dot($array);

// ['products.desk.price' => 100]
```

### `array_except()`
<a name="array_except"></a>

The `array_except` function removes the given key / value pairs from an array:

```php
$array = ['name' => 'Desk', 'price' => 100];

$filtered = array_except($array, ['price']);

// ['name' => 'Desk']
```

### `array_first()`
<a name="array_first"></a>

The `array_first` function returns the first element of an array passing a given truth test:

```php
$array = [100, 200, 300];

$value = array_first($array, function ($key, $value) {
    return $value >= 150;
});

// 200
```

### `array_last()`
<a name="array_last"></a>

The `array_last` function returns the last element of an array passing a given truth test:

```php
$array = [100, 200, 300, 110];

$last = array_last($array, function ($key, $value) {
    return $value >= 150;
});

// 300
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
