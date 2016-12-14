## What is it?

This is a plugin for [Owlcarousel](https://github.com/OwlFonk/OwlCarousel) `javascript` library for loading your slide content from
some remote source i.e. thorugh API.

**Why would you use it?** Well in my case this page I was designing had a lot of images, slider and carousal.
The waiting time was too much so I decided to render the page first then look for slider contents through my API. This surely improved
performence and user experience. 

## How to use it?

Include [Owlcarousel](https://github.com/OwlFonk/OwlCarousel) and all its dependencies in your page and then include 
`owlcarousel-json-load.js` file afterwards.

    <script type="text/javascript" src="/path/to/owlcarousel-json-load.js"></script>


## Parameters

This plugin introduces three additional parameters with the default ones-

- `path`: path to remote resource
- `onSuccess`: callback function after the remote data is loaded
- `onError`: callback function if there is any error while loading the remote data


## Example

Assume your remote data is

```
[
    {
        title: 'Some Title',
        image: 'url/to/some/image.jpeg'
    },
    {
        title: 'Some Title',
        image: 'url/to/some/image.jpeg'
    },
    {
        title: 'Some Title',
        image: 'url/to/some/image.jpeg'
    }
]
```


```
jQuery(document).ready(function($){
    var owlDemoCarousel = $('#owl-demo').owlCarousel({
        // owl default parameters
        
        path : 'path/to/remote/resource',
        onSuccess : function(data){
            //  json data loaded, 
            //  format your template, 
            //  add each in the original slider and reinitialize the carousel.

            if( data.length > 0 ){
                for( var i in data ){
                    if( data.hasOwnProperty(i) ){
                        var $html = '';

                        //  prepare the html of each slide item, wrap it with jquery and pass it in this custom event. 
                        owlDemoCarousel.trigger('add.owl.carousel', jQuery($html) )
                    }
                }
                //  Again refresh the carousel to make it aware of the newly added slides, otherwise it wouldn't care
                owlDemoCarousel.trigger('refresh.owl.carousel');
            }
        },
        onError: function(r){
            console.error(r);
        }
    });
});
```

__Note:__ This code would work on the current version of [Owlcarousel](https://github.com/OwlFonk/OwlCarousel). I can not guarrenty of
the usability if the parent library changes its way of behaviour, namely plugin binding mechanism, events etc. But I'd try to keep up 
with the changes.


## Future

Note: This plugin is still in a basic stage. You still need to manually add your slides and reinitialize the carousal
in your success callback. In future I do hope to remove all these limitations. I hope to integrate something to allow 
micro templating so that once you pass your template then it would do all other stuffs by itself.  


