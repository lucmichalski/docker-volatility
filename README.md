![VOL-logo](https://raw.githubusercontent.com/blacktop/docker-volatility/master/logo.png) Volatility Dockerfile
==================

[![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org)
[![Docker Stars](https://img.shields.io/docker/stars/blacktop/volatility.svg)][hub]
[![Docker Pulls](https://img.shields.io/docker/pulls/blacktop/volatility.svg)][hub]
[![Image Size](https://img.shields.io/imagelayers/image-size/blacktop/volatility/latest.svg)](https://imagelayers.io/?images=blacktop/volatility:latest)
[![Image Layers](https://img.shields.io/imagelayers/layers/blacktop/volatility/latest.svg)](https://imagelayers.io/?images=blacktop/volatility:latest)

This repository contains a **Dockerfile** of [Volatility](https://github.com/volatilityfoundation/volatility) for [Docker](https://www.docker.io/)'s [trusted build](https://hub.docker.com/r/blacktop/volatility/) published to the public [Docker Registry](https://hub.docker.com/).

### Dependencies

* [blacktop/yara](https://registry.hub.docker.com/u/blacktop/yara/)

### Image Tags
```bash
$ docker images

REPOSITORY                 TAG           VIRTUAL SIZE
blacktop/volatility        latest        117 MB
blacktop/volatility        2.5           114 MB
blacktop/volatility        2.4           136 MB
```

### Installation

1. Install [Docker](https://www.docker.io/).

2. Download [trusted build](https://hub.docker.com/r/blacktop/volatility/) from public [Docker Registry](https://hub.docker.com/): `docker pull blacktop/volatility`

### Usage
```bash
$ docker run --rm -v /path/to/mem:/data:ro blacktop/volatility -f silentbanker.vmem pslist
```
> **NOTE:** To use Community Plugins add `--plugins=/plugins` option to Volatility when you run it (see [Specifying Additional Plugin Directories](https://github.com/volatilityfoundation/volatility/wiki/Volatility%20Usage#specifying-additional-plugin-directories))

#### Output
```bash
Volatility Foundation Volatility Framework 2.5
Offset(V)  Name                    PID   PPID   Thds     Hnds   Sess  Wow64 Start                          Exit
---------- -------------------- ------ ------ ------ -------- ------ ------ ------------------------------ ------------------------------
0x810b1660 System                    4      0     59      183 ------      0
0xff2ab020 smss.exe                544      4      3       21 ------      0 2010-08-11 06:06:21 UTC+0000
0xff1ecda0 csrss.exe               608    544     11      365      0      0 2010-08-11 06:06:23 UTC+0000
0xff1ec978 winlogon.exe            632    544     18      511      0      0 2010-08-11 06:06:23 UTC+0000
0xff247020 services.exe            676    632     16      269      0      0 2010-08-11 06:06:24 UTC+0000
0xff255020 lsass.exe               688    632     19      345      0      0 2010-08-11 06:06:24 UTC+0000
0xff218230 vmacthlp.exe            844    676      1       24      0      0 2010-08-11 06:06:24 UTC+0000
0x80ff88d8 svchost.exe             856    676     17      199      0      0 2010-08-11 06:06:24 UTC+0000
0xff217560 svchost.exe             936    676     10      270      0      0 2010-08-11 06:06:24 UTC+0000
0x80fbf910 svchost.exe            1028    676     71     1355      0      0 2010-08-11 06:06:24 UTC+0000
0xff22d558 svchost.exe            1088    676      4       79      0      0 2010-08-11 06:06:25 UTC+0000
0xff203b80 svchost.exe            1148    676     14      208      0      0 2010-08-11 06:06:26 UTC+0000
0xff1d7da0 spoolsv.exe            1432    676     13      135      0      0 2010-08-11 06:06:26 UTC+0000
0xff1b8b28 vmtoolsd.exe           1668    676      5      222      0      0 2010-08-11 06:06:35 UTC+0000
0xff1fdc88 VMUpgradeHelper        1788    676      4      100      0      0 2010-08-11 06:06:38 UTC+0000
0xff143b28 TPAutoConnSvc.e        1968    676      5      100      0      0 2010-08-11 06:06:39 UTC+0000
0xff25a7e0 alg.exe                 216    676      6      105      0      0 2010-08-11 06:06:39 UTC+0000
0xff364310 wscntfy.exe             888   1028      1       27      0      0 2010-08-11 06:06:49 UTC+0000
0xff38b5f8 TPAutoConnect.e        1084   1968      1       61      0      0 2010-08-11 06:06:52 UTC+0000
0xff3865d0 explorer.exe           1724   1708     12      317      0      0 2010-08-11 06:09:29 UTC+0000
0xff3667e8 VMwareTray.exe          432   1724      1       49      0      0 2010-08-11 06:09:31 UTC+0000
0xff374980 VMwareUser.exe          452   1724      7      192      0      0 2010-08-11 06:09:32 UTC+0000
0x80f94588 wuauclt.exe             468   1028      4      135      0      0 2010-08-11 06:09:37 UTC+0000
0x80f1b020 IEXPLORE.EXE           1884   1724      9      351      0      0 2010-08-15 18:54:05 UTC+0000
0xff3856c0 cmd.exe                1136   1668      0 --------      0      0 2010-08-15 19:01:51 UTC+0000   2010-08-15 19:01:51 UTC+0000
```

### To Run on OSX
 - Install [Homebrew](http://brew.sh)

```bash
$ brew install caskroom/cask/brew-cask
$ brew cask install virtualbox
$ brew install docker
$ brew install docker-machine
$ docker-machine create --driver virtualbox default
$ eval $(docker-machine env default)
```
Add the following to your bash or zsh profile

```bash
alias vol='docker run -it --rm -v $(pwd):/data:ro blacktop/volatility $@'
```

[hub]: https://hub.docker.com/r/blacktop/volatility/
