denymount
=========

Node.js library to prevent automatic mounting of specific disks on Mac OS X.
For Mac OS X >= 10.9.

***

Usage
-----

```js
var denymount = require('denymount');
var cancelFn = denymount(diskName, function(error) {
  if (!error) {
    console.log('Mount denied successfully');
  } else {
    console.error('Failed to deny mount: ' + error);
  }
});
```

``diskName`` above is the disk's *identifier*, which you may find with
``diskutil list``.

Development
-----------

denymount wraps a native command line utility that must be built with Xcode 7.
If you make edits to the executable source make sure to build it afterwards
with:

```sh
$ ./build.sh
```

This will build and place the compiled executable in the *bin* folder.

The command line utility can be used directly as follows:

```sh
$ ./bin/denymount diskName
```

The programme will keep running until the given disk appears or you hit
``ctrl+C`` (or SIGINT/SIGTERM if sent to background).

Support
-------

If you're having any problem, please [raise an issue](https://github.com/resin-io/denymount/issues/new)
on GitHub and the Resin.io team will be happy to help.

License
-------

*denymount* is free software, and may be redistributed under the terms specified
in the [license](https://github.com/resin-io/denymount/blob/master/LICENSE).
