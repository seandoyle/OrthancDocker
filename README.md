# Orthanc for Docker

[Docker Hub](https://www.docker.com/) repository to build
[Orthanc](http://www.orthanc-server.com/) and its official
plugins. Orthanc is a lightweight, RESTful Vendor Neutral Archive for
medical imaging.

Full documentation is available in the
[Orthanc Book](http://book.orthanc-server.com/users/docker.html).

The content of this Docker repository is licensed under the AGPLv3+
license.

Note: This fork contains several small changes so that docker instances can be created for the Raspberry Pi 4 (64 bit OS). The original repo is focused on on LSB (Linux Standard Base) binaries for AMD64 systems. Very little is changed here - instead of pre-compiled binaries being loaded into docker files the files are compiled for source. It takes a while on a Raspberry Pi w/4GB RAM.

Other changes include changing the base image from ubuntu:14.04 to ubuntu:22.04 and the version of Python from 3.7 to 3.10.12. Also - the calls to mercurial (e.g., 'hg') have all been replaced with wget calls to the zip files for the source (such as 'https://www.orthanc-server.com/downloads/get.php?path=/plugin-dicom-web/OrthancDicomWeb-1.15.tar.gz') because the mercurial URLs returned 404 messages.

There are some other minor changes made in the installed packages. These were made simply to get the system to compile. Also - changes were only made in the base, orthanc, orthanc-plugins-big, and orthanc-python subdirectories. Little testing has been done except that simple python programs run successfully.

The orthanc-big, orthac-debug, orthanc-tests, wasm subfolders have not been modified and will not work with the Raspberry Pi without some (minor) additional work.

To build the Orthanc image with the python plugin - follow these steps:

cd base
./build.sh

cd ../orthanc-plugins-big
./build.sh
4892 seconds to build image `raspi/orthanc-big'

cd ../orthanc-python
./build.sh
118 seconds to build image `raspi/orthanc-python'


