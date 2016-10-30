Chroma Gallery
==============

Chroma Gallery is an image gallery that allows you to organize your photos into grids and enlarge them elegantly, 
in addition to using the predominant color to highlight the visual.

Licence: under the MIT license: http://www.opensource.org/licenses/mit-license.php

- [Dependencies](#dependencies)
- [How to use](#how-to-use)
- [Requirements](#requirements)
- [Options](#options)
- [Methods](#methods)
- [Callbacks](#callbacks)
- [Tips and Tricks](#tips-and-tricks)

[demo](http://codecrafting.net/chromagallery/dist)

## Dependencies

Chroma Gallery has 2 dependencies:

*   [Jquery](https://jquery.com)
*   [Masonry](http://masonry.desandro.com)

## How to use

To get started, download the plugin (dist folder), unzip it and copy files to your website/application directory.
Add the javascript files to your html. Make sure you also add the jQuery library.
    
    <script src="scripts/modernizr-chrg.min.js"></script>
    <script src="scripts/masonry.min.js"></script>
    <script src="scripts/chromagallery.min.js"></script>

You can also use the package version that includes all dependencies

    <script src="scripts/chromagallery.pkgd.min.js"></script>

Add the css file to your html.

    <link rel="stylesheet" href="stylesheets/chromagallery.min.css">

Note that css uses a font icon, make sure your directory structure is aligned with the css.

The HTML markup is really minimal. Create a div element that will surround all gallery grid and add img tags as
you want

    <div class="chroma-gallery mygallery">
        <img src="images/thumbs/1.jpg" alt="Pic 1" data-largesrc="images/1.jpg">
        <img src="images/thumbs/2.jpg" alt="Pic 2" data-largesrc="images/2.jpg">
        <img src="images/thumbs/3.jpg" alt="Pic 3" data-largesrc="images/3.jpg">
        <img src="images/thumbs/4.jpg" alt="Pic 4" data-largesrc="images/4.jpg">
        <img src="images/thumbs/5.jpg" alt="Pic 5" data-largesrc="images/5.jpg">
        <img src="images/thumbs/6.jpg" alt="Pic 6" data-largesrc="images/6.jpg">
        <img src="images/thumbs/7.jpg" alt="Pic 7" data-largesrc="images/7.jpg">
        <img src="images/thumbs/8.jpg" alt="Pic 8" data-largesrc="images/8.jpg">
        <img src="images/thumbs/9.jpg" alt="Pic 9" data-largesrc="images/9.jpg">
        <img src="images/thumbs/10.jpg" alt="Pic 10" data-largesrc="images/10.jpg">
    </div>

Pay attention to alt and data-largesrc attributes. The Alt attribute will be used to add the
descriptions of the image. The data-largesrc is src path to larger version of the image.

You do not need to add the chroma-gallery class, but it's better to prevent images from being displayed prematurely.

You can add multiples galleries too.

To initialize the gallery use a script like this:

    <script type="text/javascript">
        $(".mygallery").chromaGallery(};
    </script>

You can also add optional options which will extend default values. Example:

    <script type="text/javascript">
        $(".mygallery").chromaGallery
        ({
            color:'#000',
            gridMargin:15,
            maxColumns:5
            dof:true,
            screenOpacity:0.8
        });
    </script>

You can also load images from options like this:

    <script type="text/javascript">
        $(".mygallery").chromaGallery
        ({
            items:
            [
                {
                    src: 'images/thumbs/1.jpg',
                    alt:'Pic 1',
                    largesrc:'images/1.jpg'    
                },
                {
                    src: 'images/thumbs/2.jpg',
                    alt:'Pic 2',
                    largesrc:'images/2.jpg'    
                },
                {
                    src: 'images/thumbs/3.jpg',
                    alt:'Pic 3',
                    largesrc:'images/3.jpg'    
                },
                {
                    src: 'images/thumbs/4.jpg',
                    alt:'Pic 4',
                    largesrc:'images/4.jpg'    
                }
            ]
        });
    </script>

Note that if any html markup is present and you provide a optional items, only the last will be used

## Requirements

Chroma Gallery will work on the following browsers:

*   Firefox 4+
*   IE 9+
*   Google Chrome 8+
*   Safari 3.1+
*   Opera 11.5+
*   IOS Safari 3.2+
*   Android Browser 2.1+
*   Opera Mobile 12+

Chroma Gallery requires Jquery 1.4.3+ 

## Options

You can use the following options

Name | Type | Default Value | Description
------------ | ------------ | ------------- | -------------
color | String | chroma | Set the color of the background. If the value is "chroma" will be the predominant color of the image
maxColumns | Number |  4 | The max number of the columns on the grid. If the number is not possible the value will be override
items | Array | null | A array that contains the img items to be loaded
dof | boolean | false | Ads a Depth of Field effect to the background. Can hit performance
screenOpacity | Number | 0.95 | The screen opacity between 0 and 1
lazyLoad | boolean | true | Add or not the lazy load effect on the grid
gridMargin | Number | 7 | Set the grid margin between the images
fullscreen | boolean | false | Add or not the fullscreen mode
easing | String | easeInOutQuart | Set the easing mode for the open and close animations. Check below all values possible

Easing options:

*   linear
*   ease
*   easeIn
*   easeOut
*   easeInOut
*   easeInQuad
*   easeInCubic
*   easeInQuart
*   easeInQuint
*   easeInSine
*   easeInExpo
*   easeInCirc
*   easeInBack
*   easeOutQuad
*   easeOutCubic
*   easeOutQuart
*   easeOutQuint
*   easeOutSine
*   easeOutExpo
*   easeOutCirc
*   easeOutBack
*   easeInOutQuad
*   easeInOutCubic
*   easeInOutQuart
*   easeInOutQuint
*   easeInOutSine
*   easeInOutExpo
*   easeInOutCirc
*   easeInOutBack

## Methods

You can use the following methods

Name | Parameter | Description
------------ | ------------- | ------------
openImg | the index number of the image | Open a image from grid
closeImg | none | Close any opened image
goTo | the index number of the img | Go to a specific image when any image is already opened
next | none | Go to next image
prev | none | Go to previous image

Example:

    <script type="text/javascript">
        var mygallery = $(".mygallery").chromaGallery();

        //will open the third
        mygallery.chromaGallery("openImg",2);
    </script>

## Callbacks

You can use the following callbacks

Name | Description
------------ | -------------
onLoad | On the gallery grid load
onOpen | On a image open
onClose | On a image close
onNext | On go to next image
onPrev | On go to previous image
onFullscreen | On go to fullscreen mode if available

Example:

    <script type="text/javascript">
        $(".mygallery").chromaGallery
        ({
            onLoad:function()
            {
                this.chromaGallery("openImg",2);
            }
        });
    </script>

## Tips and Tricks

Check the following tips:

*   Use small thumbnail to minimize the impact of getting the predominant color.
*   Pay atention to the size of the div that wraps your images. The Chroma Gallery will follow the size of his parent.
*   Use onLoad callback to call any method or for any extra code.
*   Feel free to customize the font of the image description and/or the index when a image is opened.
*   Don't worry if a image is broken, the Chroma Gallery will handle it
*   Pay attention to stylesheets and fonts folders. The css must correctly reference the chroma-ui font location.

You should consider to not use the Chroma Gallery when:

*   Don't want to enlarge your image. If you want a grid layout, use masonry alone.
*   If you have large image description. Chroma Gallery limits the description in 144 characters.
*   If you need to seperate a page to your image.
*   Your image size (MB) is too large.