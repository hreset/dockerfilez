FROM ubuntu:15.04
MAINTAINER Henson Sturgill <henson.reset@gmail.com>

# Install dependencies for our image
RUN apt-get update && apt-get install qemu-system-arm unzip -y

# Pull down custom kernel, and custom raspbian image
ADD http://xecdesign.com/downloads/linux-qemu/kernel-qemu /tmp/
ADD http://goo.gl/mrKD3t /tmp/raspbian.zip
WORKDIR /tmp
RUN unzip raspbian.zip; rm raspbian.zip

# Run the emulator
EXPOSE 3333
CMD qemu-system-arm -kernel kernel-qemu -cpu arm1176 -m 256 -M versatilepb -no-reboot -serial stdio -append "root=/dev/sda2 panic=1 rootfstype=ext4 rw" -hda 2015-02-16-raspbian-wheezy.img -curses -redir tcp:3333::22 

