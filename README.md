# Knowledge

## Command Line Programs and Utilities

### Direct Print PDF - `SumatraPDF`

Use [SumatraPDF](https://github.com/sumatrapdfreader/sumatrapdf) to direct print PDF Files

```shell
C:/path/SumatraPDF-3.5.2-64.exe -print-to "<print_name>" <path/file.pdf>
```

### Convert imagens to many formats - `magick`

Description: *ImageMagick® is a free, open-source software suite, used for editing and manipulating digital images. It can be used to create, edit, compose, or convert bitmap images, and supports a wide range of file formats, including JPEG, PNG, GIF, TIFF, and PDF.*
Project: http://www.imagemagick.org/

```shell
magick -debug command file.pdf -define jpeg:size=48x48 -background #FFFFFF -flatten -thumbnail 48x48 image.48.48.png
```

## GIT

###  `Gittyup` - Graphical Git client designed by github creator

Description: *Gittyup is a graphical Git client designed to help you understand and manage your source code history. The latest stable release is available either as pre-built flatpak for Linux, 32 / 64 binary for Windows, macOS, or can be built from source by following the directions below.*
Proejct: https://github.com/Murmele/Gittyup

![alt text](https://raw.githubusercontent.com/Murmele/Gittyup/master/rsrc/screenshots/main_dark_orig.png?raw=true)

