# stopsopa/elkanatooltip

Yet another toolbar jQuery plugin, but this time with full api control 

## Usage, demo & css generator

  [Demo](http://stopsopa.github.io/submod/elkanatooltip/demo.html)

***

## Npm instalation 

<a href="https://www.npmjs.com/package/elkanatooltip">
<img width="60" src="https://www.npmjs.com/static/images/npm-logo.svg">
</a>



### Api description

First follow instructions of installation on [npm](https://www.npmjs.com/package/elkanatooltip) and [demo](http://stopsopa.github.io/submod/elkanatooltip/demo.html).
Then you need to understand few things:


#### you can have multiple tooltip styles on one pages by [generating](http://stopsopa.github.io/submod/elkanatooltip/generator.html) separate css files. The only requirements is to have different [class name](http://stopsopa.github.io/submod/elkanatooltip/generator.html?tour=.controls%20tr:first%20input) in each css file (this is some kind of namespace or id for each style). 
Then you can include styles like this ...


  
```html
<script src="jquery.js"></script>
<script src="jquery.elkanatooltip.js"></script>
<link rel="stylesheet" type="text/css" href="elkanatooltip_first-style-class_1457790488968.css" />
<link rel="stylesheet" type="text/css" href="elkanatooltip_second-style-class_1457790488968.css" />        
```  

... and after that you are ready to use each style like below :


```javascript

var options = {
    "position": {
        "my": "top",
        "at": "bottom"
    }
};

var dct = $('.default-style-class-target');
var dci = $('.default-style-class-tip');
dct.elkanatooltip(dci, options); // class will be default: 'elkanatooltip'

var fct = $('.first-style-class-target');
var fci = $('.first-style-class-tip');
fct.elkanatooltip(fci, options, 'first-class'); 

var sct = $('.second-style-class-target');
var sci = $('.second-style-class-tip');
sct.elkanatooltip(sci, options, 'first-class'); 
    
```  

#### show hide

If tooltip is already initialized, then you can show or hide tooltip:

```javascript
target.elkanatooltip(true); // show
target.elkanatooltip(false); // hide    
```  

Current state (if tooltip is visible or hidden) you can get under:
 
```javascript
target.elkanatooltip().show;    
```  

So you can easly toggle tooltip
 
```javascript
target.elkanatooltip( ! target.elkanatooltip().show);   
```  

If target is moving around page (for example it is draggable element) to reposition tooltip again on target simply do ...

```javascript
target
    .draggable({ 
        drag: function () { 
            target.elkanatooltip(true);
        }
    });
```  

... or even better to get more consist positioning (you don't need to worry about existence of process.nextTick, it is polifiled by elkanatooltip itself) ...

```javascript
target
    .draggable({ 
        drag: function () {                        
            process.nextTick(function() {
                target.elkanatooltip(true);
            })
        }
    });
```  

 





 





### License

The MIT License (MIT)
Copyright (c) 2016 Szymon Działowski
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

