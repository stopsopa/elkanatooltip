# DEPRECATED
Created in 2016 - quite old now and not maintained.

# demo
- [demo.html](http://stopsopa.github.io/elkanatooltip/demo.html)
- [katownik.html](http://stopsopa.github.io/elkanatooltip/katownik.html)

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
<link rel="stylesheet" type="text/css" href="elkanatooltip_first-style-class.css" />
<link rel="stylesheet" type="text/css" href="elkanatooltip_second-style-class.css" />        
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
sct.elkanatooltip(sci, options, 'second-class'); 
    
```  

#### show hide

If tooltip is already initialized, then you can show or hide tooltip:

```javascript
target.elkanatooltip(true); // show
target.elkanatooltip(false); // hide    
```  

You can examine - if tooltip is visible or hidden - under:
 
```javascript
target.elkanatooltip().show;    
```  

... so you can easly toggle tooltip by ...
 
```javascript
target.elkanatooltip( ! target.elkanatooltip().show);   
```  

.. or using special method for that:
 
```javascript
target.elkanatooltip('toggle');   
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

* this draggable examples require [jQuery UI draggable](//jqueryui.com/draggable/)

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
 

#### correction

It is possible to adjust position of tooltip manually during initialization:



```javascript
var options = {
    "ui": {
        "my": "top",
        "at": "bottom"
    },
    offset: {
        left: 20,
        top: -10
    }
};

var dct = $('.default-style-class-target');
var dci = $('.default-style-class-tip');
dct.elkanatooltip(dci, options);

```  

#### destroy

To destroy component and reverse all states of divs simply call 


```javascript
var dct = $('.default-style-class-target');
dct.elkanatooltip('destroy');

```  

#### events 

afterShow and afterHide are triggered at the end of css show or hide animation (if animations are defined, if they are not defined, events are called immediately)

```javascript

var options = {
    position: {
        my: "top",
        at: "bottom"
    },
    afterShow: function () {
        // eg: $(this).elkanatooltip().show
    },
    afterHide: function () {
        // eg: $(this).elkanatooltip().show
    }
};

...

``` 

#### within 

Element to position within, affecting collision detection. If you provide a selector or jQuery object, the first matching element will be used.

```javascript

var options = {
    position: {
        my: "top",
        at: "bottom",
        within: $('.selector')
    }
};

...

``` 

 
## Tips
 
Elkanatooltip is designed in way that allow You to customize manually entire view in css, that includes also style of animation on hiding or showing tooltip (this was not easy to implement). These type of manual modification of css file shouldn't spoil any behaviour of plugin, so i encourage You to do that.

Most of chenges can be done manually in css, for all rest what must be done with proper recalculations You can make by [generatior](http://stopsopa.github.io/submod/elkanatooltip/generator.html).

Notice that in the first line of generated file is permalink that You can use to restore all states of generator in order to adjust previousely made style.
 
This plugin is low level of future tools. Main job of this tool is to create tooltip on top of pointed div, show, hide (with animation or not) and reposition this tooltip. 

Any bugs reports or pull request are welcome.

Cheers :)


### License

The MIT License (MIT)
Copyright (c) 2016 Szymon Działowski
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


