+++
title = '如何在MAC中製作Windows 10的重灌USB'
date = '2017-04-03T17:35:50+08:00'
draft = false
+++

最近學習使用Python來作點AI的事，發現好多最新的套件都是在Linux上才有，所以換了Ubuntu 18.04來玩玩。但是對於我這個習慣使用Mac來作文書作業的苦手，終究受不了Linux上的一些問題，且，**電腦是拿來用的，不是拿來折騰的**。最後決定把我的桌機再重新灌回Windows 10來使用(Linux基本教義派別打我)，但發了一整個晚上，一直沒有辦法順利的重灌。
灌個windows10哪有這麼難，主要是卡關在Mac上製作可開機USB碟，在忙呼了一整晚，過程中經歴中線上會議與老婆的查勤電話，終於最後找到原因，並解決了。
以下記錄一下這次的心得。
<!--more-->
## 環境

### 作業系統

- MacOS 10.15.4 Catalina  
- Windows10檔案: [Win10_Edu_1909_Chinese(Traditional)_x64.iso](https://www.microsoft.com/zh-tw/software-download/vlacademicwindows10iso)  

### 軟體

- Bootcamp
- balenaEthcer 1.5.71
- unetbootin

### USB

- Transcend 8GB USB Disk  

### PC主機板

- Gigabyte G1-Sniper-H6  

### CPU

- Intel-4790k

## 用Boot Camp Assistant製作

USB可以跑完，程式完整，但不能開機。

## 用ubnet

可以跑完，可以開機，但安裝會報錯，有一個檔案無法正常讀取。

## 作個撒尿牛丸

- 先將USB格式化成exfat
- 再用bootcamp安裝windows程式
- 再跑一次ubnet，一路按跳過，最後製作開機檔
完工~
