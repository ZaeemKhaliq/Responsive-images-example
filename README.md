# Responsive-images-example

Responsive images implementation using HTML ```img```'s ```srcset``` and ```sizes``` attribute.

The important element in this implementation is **viewport width**. The image sizes set through CSS don't affect which image loads in the browser.

The ```srcset``` takes in a comma-separated values of _image URLs_ along with their _descriptor_ which defines the width of the image. Example:

~~~
srcset="my-320-image 320w,
        my-640-image 640w,
        my-1024-image 1024w"
~~~
Here, **320w**, **640w** and **1024w** are **width descriptors** (the other is **pixel descriptor** which is used like **1x**, **2x**, **3x** etc.), which specifies the image's width relative to viewport. So when the viewport's width value in px is less than and equal to **320px**, the **320w** one will be used.

The ```sizes``` attribute controls the intended display size of the image according to viewport, as opposed to the rendered size (CSS width and height). It takes a comma-separated values consisting of _media condition_ and _image width_. For example:

~~~
sizes="(min-width: 601px) 33vw, 100vw"
~~~
Here we specify the image's size as 33vw when display is larger than **601px**, and 100vw when less than that. This attribute controls which of the ```srcset```'s value gets used.

For example, if the display/viewport width is **640px** wide, and image's ```sizes``` attribute is set to ```33vw```, then 33% of 640 is approx. 211. Which means at **640px**, image's size is **211px**.
Now out of the three ```srcset``` we listed, it would use the **320w** one, since **211px**(image's size due to **sizes** attribute) is less than **320**.
If we used ```sizes="100vw"```, at **640px** the image's width will be **640px**, and hence the second **640w** from the ```srcset``` would be used.
