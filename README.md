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
  * [array_flatten()](#array_flatten)
  * [array_forget()](#array_forget)
  * [array_get()](#array_get)
  * [array_set()](#array_set)
  * [array_has()](#array_has)
  * [array_only()](#array_only)
  * [array_pluck()](#array_pluck)
  * [array_pull()](#array_pull)
  * [array_where()](#array_where)
  * [data_get()](#data_get)
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

### `array_flatten()`
<a name="array_flatten"></a>

The `array_flatten` function flattens a multi-dimensional array into a single level array:

```php
$array = ['name' => 'Joe', 'languages' => ['PHP', 'Ruby']];

$flattened = array_flatten($array);

// ['Joe', 'PHP', 'Ruby']
```

### `array_forget()`
<a name="array_get"></a>

The `array_forget` function removes a given key / value pair from a deeply nested array using "dot" notation:

```php
$array = ['products' => ['desk' => ['price' => 100]]];

array_forget($array, 'products.desk');

// ['products' => []]
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

## `array_has()`
<a name="array_has"></a>

The `array_has` function checks whether a given item or items exists in an array using "dot" notation:

```php
$array = ['product' => ['name' => 'Desk', 'price' => 100]];

$contains = array_has($array, 'product.name');

// true

$contains = array_has($array, ['product.price', 'product.discount']);

// false
```

### `array_only()`
<a name="array_only"></a>

The `array_only` function returns only the specified key / value pairs from the given array:

```php
$array = ['name' => 'Desk', 'price' => 100, 'orders' => 10];

$slice = array_only($array, ['name', 'price']);

// ['name' => 'Desk', 'price' => 100]
```

### `array_pluck()`
<a name="array_pluck"></a>

The `array_pluck` function retrieves all of the values for a given key from an array:

```php
$array = [
    ['developer' => ['id' => 1, 'name' => 'Taylor']],
    ['developer' => ['id' => 2, 'name' => 'Abigail']],
];

$names = array_pluck($array, 'developer.name');

// ['Taylor', 'Abigail']
```

You may also specify how you wish the resulting list to be keyed:

```php
$names = array_pluck($array, 'developer.name', 'developer.id');

// [1 => 'Taylor', 2 => 'Abigail']
```

### `array_pull()`

The `array_pull` function returns and removes a key / value pair from an array:

```php
$array = ['name' => 'Desk', 'price' => 100];

$name = array_pull($array, 'name');

// $name: Desk

// $array: ['price' => 100]
```

A default value may be passed as the third argument to the method. This value will be returned if the key doesn't exist:

```php
$value = array_pull($array, $key, $default);
```

### `array_where()`

The `array_where` function filters an array using the given Closure:

```php
$array = [100, '200', 300, '400', 500];

$filtered = array_where($array, function ($value, $key) {
    return is_string($value);
});

// [1 => '200', 3 => '400']
```

### `data_get()`
<a name="data_get"></a>

The `data_get` function retrieves a value from a nested array or object using "dot" notation:

```php
$data = ['products' => ['desk' => ['price' => 100]]];

$price = data_get($data, 'products.desk.price');

// 100
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
