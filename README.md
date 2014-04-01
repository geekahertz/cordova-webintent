# WebIntent Android Plugin for Cordova 3.X #
By Boris Smus

Please see the original plugin at the [WebIntent](https://github.com/Initsogar/cordova-webintent) plugin site.

## Adding the Plugin to your project ##
1. To install the plugin, use the Cordova CLI and enter the following:

`cordova plugin add https://github.com/geekahertz/cordova-webintent.git`

2. Confirm that the following is in your `res/xml/config.xml` file:

`<plugin name="WebIntent" value="com.borismus.webintent.WebIntent" />`

## Sample code

Here is an example of using webintent to select a file chooser, pick a file, which then return the uri in an JSON Object:

    window.plugins.webintent.startActivityForResult(
        {
            action: "android.intent.action.GET_CONTENT",
            type : "*/*"        
        },
        function() {data},
            alert(JSON.stringify(data));
        function() {
            alert('Failed to retrieve uri via Android Intent.');
        }
    );

Here is an example of using webintent to scan a barcode (provided you have zxing barcode scanner installed)

    window.plugins.webintent.startActivityForResult(
        {
            action: "com.google.zxing.client.android.SCAN"
        },
        function() {data},
            alert(JSON.stringify(data));
        function() {
            alert('Failed to retrieve uri via Android Intent.');
        }
    );


## Additional method for this plugin ##
The plugin creates the object `window.plugins.webintent` with five methods:

### startActivityForResult ###
Launches an Android intent and return the uri / extras as a JSON object. For example:

    window.plugins.webintent.startActivityForResult(
        {
            action: "android.intent.action.GET_CONTENT",
            type : "*/*"        
        },
        function(data) {
            alert(JSON.stringify(data));
        },
        function() {
            alert('Failed to open URL via Android Intent')
        };
    );

## Licence ##

The MIT License

Copyright (c) 2010 Boris Smus

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
