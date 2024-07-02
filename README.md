# Knowledge Base

# Command Line Programs and Utilities

## `SumatraPDF` - Direct Print PDF

Description: *Use [SumatraPDF](https://github.com/sumatrapdfreader/sumatrapdf) to direct print PDF Files*

Project: https://github.com/sumatrapdfreader/sumatrapdf

```shell
C:/path/SumatraPDF-3.5.2-64.exe -print-to "<print_name>" <path/file.pdf>
```

## `magick` - Convert imagens to many formats

**Description**: *ImageMagick® is a free, open-source software suite, used for editing and manipulating digital images. It can be used to create, edit, compose, or convert bitmap images, and supports a wide range of file formats, including JPEG, PNG, GIF, TIFF, and PDF.*

**Project**: http://www.imagemagick.org/

```shell
magick -debug command file.pdf -define jpeg:size=48x48 -background #FFFFFF -flatten -thumbnail 48x48 image.48.48.png
```

## `syncthing` - It synchronizes files between two or more computers in real time, safely protected from prying eyes

**Description**: *Syncthing is a continuous file synchronization program. It synchronizes files between two or more computers in real time, safely protected from prying eyes. Your data is your data alone and you deserve to choose where it is stored, whether it is shared with some third party, and how it’s transmitted over the internet.*

**Project**: https://syncthing.net/

**How to use/Install**: https://www.youtube.com/watch?v=zU5sisowCgw


## `scoop` - A command-line installer for Windows

**Description**: *Scoop installs programs you know and love, from the command line with a minimal amount of friction. It: Eliminates permission popup windows; Hides GUI wizard-style installers; Prevents PATH pollution from installing lots of programs; Avoids unexpected side-effects from installing and uninstalling programs; Finds and installs dependencies automatically; Performs all the extra setup steps itself to get a working program;*

**Project**: https://scoop.sh/

**How to use/Install**: https://scoop.sh/ (on the site has more information)



## `makeself` - Make self-extractable archives on Unix

**Description**: *makeself.sh is a small shell script that generates a self-extractable compressed tar archive from a directory. This is pretty similar to archives generated with WinZip Self-Extractor in the Windows world.*

**Project**: https://github.com/megastep/makeself

**How to use/Install**: https://github.com/megastep/makeself?tab=readme-ov-file#usage



# GIT

## `gitbutler` - Git client created by github creator

**Description**: *A Git client for simultaneous branches on top of your existing workflow.*

**Project**: https://gitbutler.com/

![gitbutler image](https://blog.gitbutler.com/content/images/size/w1600/2024/04/CleanShot-2024-04-10-at-10.48.17@2x.png?raw=true)

##  `Gittyup` - Graphical Git client 

**Description**: *Gittyup is a graphical Git client designed to help you understand and manage your source code history. The latest stable release is available either as pre-built flatpak for Linux, 32 / 64 binary for Windows, macOS, or can be built from source by following the directions below.*

**Project**: https://github.com/Murmele/Gittyup

![gittyup image](https://raw.githubusercontent.com/Murmele/Gittyup/master/rsrc/screenshots/main_dark_orig.png?raw=true)


# Host/Do yourself

## Softwares

### `NextCloud` - Nextcloud gives you access to all your files wherever you are. Hosted by you.

**Description**: *Nextcloud gives you access to all your files wherever you are. Who owns your photos and documents? Right, it should be you. With self-hosted cloud storage, your data is where you want it to be: at home or in the cloud you trust. Nextcloud runs on that server, giving you easy access to your files from desktop and mobile devices, as well as boundless syncing and sharing across locations: FTP drive at school, a Dropbox, or a NAS you have at home. Nextcloud is free and open source*

**Project**: https://nextcloud.com/  - https://github.com/nextcloud

**How to use/Install**: https://github.com/nextcloud/all-in-one#how-to-use-this



### `Portainer.io` - Portainer.io allows you to manage Docker with graphical interface accessed from any browser.

**Description**: *Portainer.io is an open source web application that allows you to manage Docker containers and images through a graphical interface accessed from any browser.*

**Project**: https://docs.portainer.io/

**How to use/Install**: https://docs.portainer.io/start/install-ce/server/docker/linux
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```


## Services

### `Duck DNS` - Free dynamic DNS hosted on AWS

**Description**: *Duck DNS a Free dynamic DNS hosted on AWS*

**Project**: https://www.duckdns.org/

**How to use/Install**: https://www.duckdns.org/domains



### `ddclient` - Updates dynamic DNS entries

**Description**: *ddclient updates dynamic DNS entries for accounts on a wide range of dynamic DNS services.*

**Project**: https://ddclient.net/

**How to use/Install**: https://ddclient.net/



