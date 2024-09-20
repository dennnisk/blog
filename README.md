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


## `Burp Suite` - Traffic Interception and Manipulation

**Description**: *Traffic Interception and Manipulation: Burp Suite acts as a web proxy that allows you to intercept and modify HTTP/HTTPS requests and responses between the client and the server. This makes it easier to identify vulnerabilities and understand network traffic.*

**Project**: https://portswigger.net/burp/communitydownload

**How to use/Install**: . . . 


## `Tesseract OCR` - Tesseract Open Source OCR Engine

**Description**: *Tesseract is tool to recognizing character patterns (OCR). 4 version use new neural net (LSTM) based OCR engine which is focused on line recognition, but also still supports the legacy Tesseract OCR engine of Tesseract 3 which works by recognizing character patterns.*

**Project**: https://github.com/tesseract-ocr/tesseract

**How to use/Install**: https://github.com/tesseract-ocr/tesseract?tab=readme-ov-file#running-tesseract



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

### `youtube-dl` - youtube-dl - Download videos from www.youtube.com, music.youtube.com or other video platforms, and you can convert to mp3

**Description**: *download videos from youtube.com or other video platforms. Include playlist from music.youtube.com and convert it to mp3*

**Project**: https://github.com/ytdl-org/youtube-dl

**How to use/Install**: https://github.com/ytdl-org/youtube-dl

```bash
.\youtube-dl.exe -o "folder\%(artist)s-%(title)s.%(ext)s" https://music.youtube.com/playlist?list=XXyy(...)luIY -x --audio-format mp3 --audio-quality 0 --cookies .\music.youtube.com_cookies.txt --sleep-interval 3 --max-sleep-interval 30 -i -w --playlist-random
```
#### How to Install
 - Download last .exe from: https://github.com/ytdl-org/ytdl-nightly/releases/ 
 - Download last FFmpeg (to convert video to mp3, etc) from: https://github.com/BtbN/FFmpeg-Builds/releases
   - Unzip at the same directory with `youtube-dl.exe`
 - Install software to extract the Cookies from your navigator: https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc?pli=1
   - Use to access the the login of your youtube premium account.
 - Access the directory and you can download and convert, like the example 


### `MP3Gain` - MP3Gain analyzes and adjusts mp3 files so that they have the same volume.

**Description**: *MP3Gain does not just do peak normalization, as many normalizers do. Instead, it does some statistical analysis to determine how loud the file actually sounds to the human ear.
Also, the changes MP3Gain makes are completely lossless. There is no quality lost in the change because the program adjusts the mp3 file directly, without decoding and re-encoding.*

**Project**: https://mp3gain.sourceforge.net/

**How to use/Install**: https://mp3gain.sourceforge.net/

```bash
If you get the error: "Component ‘MSCOMCTL.OCX’ or one if its dependencies not correctly registered: a file is missing or invalid.", try this: https://www.urtech.ca/2017/11/solved-mscomctl-ocx-download-register-64-bit-windows/
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


## Develop

### `Quarkus` - SUPERSONIC/ SUBATOMIC/ JAVA

**Description**: *A Kubernetes Native Java stack tailored for OpenJDK HotSpot and GraalVM, crafted from the best of breed Java libraries and standards.*

**Project**: https://quarkus.io/

**How to use/Install**: https://code.quarkus.io/


