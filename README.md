tire
====

Simple function chain module

Runs a chain of functions in series, each passing their results to the next.
If an error object found among arguments and error callback is specified, the next function is not executed
and the error callback is immediately called with
the error. Also supports one this object threw whole chain.

For browsers and node.js.

## Usage

`tire(fn, thisArg , errorCallback)(fn)(fn);`
* **fn** - A first and next functions to be run.
* **thisArg** - An object that will be used for this [optional].
* **errorCallback** - An callback to be run on error [optional].

##### Example

```javascript
tire(function (next) {
  fs.exists(path, next);
}, done)
(function (exists, next) {
  if(!exists) {
    var data = "uuu";
    fs.writeFile(path, data, 'utf-8', next);
  }
})
(function (err, next) {
  fs.readFile(path, 'utf-8', next);
})
(function (err, data, next) {
  fs.unlink(path, next);
})
(function () {
  done();
});
```

## License

(The MIT License)

Copyright (c) 2013 Wolf Bas &lt;becevka@kucoe.com&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

