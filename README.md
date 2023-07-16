# Docker-piCore
creating piCore docker image

Building on the work of Benjamin Henrion (http://www.zoobab.com/resume)

All of this work was completed on a Raspberry Pi 4B 8GB (Max). Current stable version of piCore is 13.0.3
Please change values as needed.

1. Download the latest picore image from here => http://www.tinycorelinux.net/ports.html
2. using Raspberry Pi Imager create boot media
3. after creation remount boot media ( usually found under /media/<username>/ )
4. open folder piCore-13
5. mkdir ~/docker-picore
6. cp ./rootfs-piCore-13.0.3.gz ~/docker-picore/rootfs-piCore-13.0.3.gz
7. cd ~/docker-picore
8. gunzip rootfs-piCore-13.0.3.gz
9. mv rootfs-piCore-13.0.3 rootfs-piCore-13.0.3.cpio
10. mkdir output
11. cd output
12. sudo cpio -idv < ../rootfs-piCore-13.0.3.cpio
13. tar -cvzf ../rootfs-piCore-13.0.3.tgz .
14. cd ..
15. docker import ./rootfs-piCore-13.0.3.tgz
16. docker images <= find the latest one with blank tags
17. docker tag <IMAGE ID> fighne/pi-core-13.0.3:latest
