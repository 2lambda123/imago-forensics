# imago-forensics 🕵️
Imago is a python tool that extract digital evidences from images recursively.
This  tool is useful throughout a digital forensic investigation. If you need to extract digital evidences and you have a lot of images, through this tool you will be able to compare them easily. Imago allows to extract the evidences into a CSV file or in a sqlite database. If in a JPEG exif are present GPS coordinates, Imago can extract the longitude and latitude and it can convert them to degrees.
Imago offers also the possibility to calculate [Error Level Analysis](https://blackhat.com/presentations/bh-dc-08/Krawetz/Whitepaper/bh-dc-08-krawetz-WP.pdf), this functionality is in BETA.

# Installation

## Installation of the requirements via pip:

To install imago requirements simply run:
```
pip install -r requirements.txt

```
## Requirements:
```
python 2.7
exifread version 2.1.2
python-magic version 0.4.15
argparse version 1.2.1
pillow version 2.7.0
```
# Usage

```
usage: imago.py [-h] -i INPUT [-x] [-g] [-e] [-n] [-d {md5,sha256,sha512,all}]
                [-o OUTPUT] [-s] [-t {jpeg,tiff}]

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT, --input INPUT
                        Input directory path
  -x, --exif            Extract exif metadata
  -g, --gps             Extract, parse and convert to coordinates, GPS exif
                        metadata from images (if any)It works only with JPEG.
  -e, --ela             Extract, Error Level Analysis image,It works only with
                        JPEG. *BETA*
  -n, --nude            Detect Nudity, It works only with JPEG, *BETA*
  -d {md5,sha256,sha512,all}, --digest {md5,sha256,sha512,all}
                        Calculate hash digest
  -o OUTPUT, --output OUTPUT
                        Output directory path
  -s, --sqli            Keep SQLite file after the computation
  -t {jpeg,tiff}, --type {jpeg,tiff}
                        Select the image, this flag can be JPEG or TIFF, if
                        this argument it is not provided, imago will process
                        all the image types(i.e. JPEG, TIFF)


```
The only required argument is -i which is the base directory from which imago will start to search for image file.
You should also provide at least one type of extraction (i.e. exif, data, gps, digest).

# Example:

```
python imago.py -i /home/solvent/cases/c23/DCIM/ -o /home/solvent/cases/c23/ -x -s -t jpeg -d all
```

Where:
* -i path: is the base directory, where imago will search for file
* -o path: the output directory where imago will save the CSV file, with the extracted metadata
* -x : imago will extract EXIF metadata.
* -s: the temporary SQLite database will not be deleted after the processing.
* -t jpeg: imago will search only for jpeg images.
* -d all: imago will calculate md5, sha256, sha512 for the jpeg images.

# Features:

| Task          | Status        |
| ------------- |:-------------:|
| Exif support  | ✔️ |
| JPEG support  | ✔️ |
| Tiff support  | ✔️ |
| Recursive directory navigation  | ✔️ |
| CSV export  | ✔️ |
| Exif support  | ✔️ |
| Sqlite export  | ✔️ |
| md5, sha256, sha512  | ✔️ |
| ELA | ✔️ BETA |
| Full GPS support  | ✔️ |
| Nudity detection  | ✔️ BETA|


# ToDo:
| Task          | Status        |
| ------------- |:-------------:|
| Filesystem metadata support  | ❌ |
| Extract images from PDF | ❌ |
| XMP support  | ❌ |


## 📑 Copyright and Licenses
Code copyright 2018 Redaelli.
Code released under the [MIT license](LICENSE).
