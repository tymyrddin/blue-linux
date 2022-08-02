# Edit exif metadata in images

## ExifTool

ExifTool is a perl program that can be used to read and edit exif metadata in images. It is available for Windows, MacOS and *nix systems.

    $ exiftool imagename.jpg 

To remove, for example GPS data (not found in the above image file, but if you have it in yours) - replace image.jpg with your image file:

    $ exiftool -gps:all= -xmp:geotag= image.jpg

## imagemagick

The mogrify command of imagemagick can be used to strip Exif data from images. For the same file as above and then checked with exiftool again:

```
$ mogrify -strip imagename.jpg
$ exiftool imagename.jpg
```

For removing Exif data from all jpg images in a directory and all of its sub-directories recursively:

    $ find ./path/directory -type f -iname '*.jpg' | xargs mogrify -strip

## exiv2

The exiv2 tool also has a command for deleting all Exif data from an image:

    $ exiv2 rm imagename.jpg

For removing Exif data from all jpg images in the current directory:

    $ exiv2 rm *.jpg

For removing Exif data from all jpg images in a directory and all of its subdirectories recursively:

    $ find ./path/directory -type f -iname '*.jpg' | xargs exiv2 rm


