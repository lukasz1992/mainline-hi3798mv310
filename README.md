# mainline-hi3798mv310

There is a very nice hisilicon chipset, used in many cheap (or not so cheap) dvb receivers running on Enigma2.
All of them are built by SDK found somewhere in github, but it relies on old 4.4 kernel.

I woke up with many ideas for using it now. I will share some of them soon.

1) Even the whole code is 32bit (starting from bootrom, bootloader, linux kernel and userspace), it is actually possible to switch it to 64bit mode! I managed to run linux kernel and userspace in aarch64, taking advantage of AES, SHA1/SHA2, CRC instructions.
This project was named "Trampoline"
2) Current drivers are very old and compatible only with HiSilicon API. I decided to take Linux 6.18 as a base and to write modern, open-source drivers that align to current kernel driver standards. The first hard work was done to allow to boot my device (Zgemma H11.S), and gain full access. While 1 GB memory is a quite a low value, it is still possible to have multimedia device.
This project was named "histb drivers" and contains: SMMU driver, DRM driver, HDMI/audio/CEC driver, stateless Video Decode Driver, stateless Postprocessor Video Driver, Demux Driver, as well as DVB frontend driver working. Some smaler/larger patches were added to reuse existing drivers, for example for USB, MMC and TRNG.

Stay tuned for code release
