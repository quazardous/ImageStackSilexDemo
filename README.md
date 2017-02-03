# Silex ImageStack Demo
A PHP image serving framework.

The main goal is to provide a robust framework to create an "on the fly" image thumbnailer generator similar to [imagecache](https://www.drupal.org/project/imagecache) / [image style](https://www.drupal.org/docs/8/core/modules/image/working-with-images) in [Drupal](https://www.drupal.org/).

Here is a demo based on [Silex](https://github.com/silexphp/Silex) .

See [SilexImageStack](https://github.com/quazardous/SilexImageStack) for more infos.

## Installation

    git clone git@github.com:quazardous/SilexImageStackDemo.git

Publish the `web` folder on an `apache` server and access it.

## Usage

We can play with [CC0](https://creativecommons.org/publicdomain/zero/1.0/deed.en) images hosted on https://pexels.com/.

I like this one https://static.pexels.com/photos/313094/pexels-photo-313094.jpeg.

Here are some tests you can make with the image stack.

NB: first image request will trigger a download from https://pexels.com/. Then thumbnails will be calculated from cached image.

A second request on the same image will be serve statically.

Original image:

    http://localhost/~you/SilexImageStackDemo/web/img/pexels/original/313094/pexels-photo-313094.jpeg

`big` style image (fit 800x500 box):

    http://localhost/~you/SilexImageStackDemo/web/img/pexels/style/big/313094/pexels-photo-313094.jpeg

`small` style image (crop to 300x200 box):

    http://localhost/~you/SilexImageStackDemo/web/img/pexels/style/small/313094/pexels-photo-313094.jpeg

`thumb` style image (crop to 100x100 box):

    http://localhost/~you/SilexImageStackDemo/web/img/pexels/style/thumb/313094/pexels-photo-313094.jpeg
    
Custom format image (use width and height from URL):

    http://localhost/~you/SilexImageStackDemo/web/img/pexels/format/200x300/313094/pexels-photo-313094.jpeg

Other will trigger `404`.

You can purge cached files removing `var/cache/pexels` (cache) and `web\img\pexels` (thumbnails).

Take a look at `app/bootstrap.php` (or here [SilexImageStack](https://github.com/quazardous/SilexImageStack)) to see it done in a few config lines in the **Silex** bootstrap.

## Credits
[quazardous](https://github.com/quazardous).

## License
MIT