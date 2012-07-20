# watch-connect

A connect middleware that force browsers to reload when the server detects file changes.

The watch mode has been borrowed from [https://github.com/mklabs/mockerie](mockerie) by the genious [mklabs](https://github.com/mklabs).

## Usage

    var Path = require('path'),
      connect = require('connect'),
      reloadOnChange = require('watch-connect');

    var path = Path.resolve('example/fixture');

    var server = connect();
    server.use(reloadOnChange(path, server, {verbose: true}));
    server.use(connect.static(path));

    server.listen(3000, function(){
      console.log('listening on http://127.0.0.1:3000');
    });

Now open your browser on the URL `http://127.0.0.1:3000`.

Look at the title color.

Now change the color in `example/fixture/sub/folder/file.css`, and save your changes.

Oh look the browser was updated :)

## Options

 * verbose: Defaults to false.  Chatty logging.
 * skipAdding: Defaults to false.  When set to true, the socket scripts will not be added to .html pages on their way through the middleware.  The assumption is that you would add them to your page(s) yourself.  This serves as a workaround for those who are not rendering .html pages directly, like express users who may be using jade templates.
 * exclude: an array of files that when changed should not cause a reload

## License

(The MIT License)

Copyright (c) 2011 Filirom1

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
