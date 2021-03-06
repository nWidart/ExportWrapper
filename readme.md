# ExportWrapper

A PHP wrapper around Sonata-Exporter, for ease of use.

## Installation

Add `nwidart/ExportWrapper` as a requirement to `composer.json`:

```
{
    ...
    "require": {
        ...
        "nwidart/ExportWrapper": "dev-master"
    },
}

```

Update composer:

```
$ php composer.phar update
```



## Usage

### Export Arrays

Prepare your array to be exported:

```
$data = [
    [
        'name' => 'Nico',
        'firstName' => 'Widart'
    ],
    [
        'name' => 'John',
        'firstName' => 'Doeeee'
    ]
];
```

Use the exporter

	use nwidart\ExportWrapper\Exporter;
Instantiation

    $exporter = new Exporter;

**Stream** data directly to the browser

	try {
        $exporter->withArray($data)->to('allusers.xlsx')->stream();
    }

And catch the exceptions

    catch (nwidart\ExportWrapper\Exceptions\IncorrectDataTypeException $e) {
        echo $e->getMessage();
    }
    catch (nwidart\ExportWrapper\Exceptions\InvalidExtensionException $e) {
        echo $e->getMessage();
    }

Or ... **export** to a location on disk

	try {
	    $exporter->withArray($data)->to('/path/to/allusers.xls')->export();
	}

With the same exceptions as the stream method.

## TODO
* Make a Laravel implementation (Service provider & Facade).



## License (MIT)

Copyright (c) 2013 [Nicolas Widart](http://www.nicolaswidart.com) , n.widart@gmail.com

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.