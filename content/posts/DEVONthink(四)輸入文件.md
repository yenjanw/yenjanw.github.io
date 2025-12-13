+++
title = 'DEVONthink(四)'
subtitle = '輸入文件/檔案'
date = '2017-04-25T17:35:50+08:00'
draft = true
tags = ['文件管理']
categories = ['DevonThink']
+++

![](http://i.imgur.com/IPr8ocy.png)

[前文](http://www.yjol.org/2017/04/18/DEVONthink(一)初步認識/)有說明到這兩者的差別，本篇文章已進入到將文件/檔案放入資料庫中，所以這裡再重新說明一下這兩者區別。

<!-- more -->

## 再次說明Import Vs. Index

- `File`->`Import`是將文件/檔案複製一份進入資料庫中。
- `File`->`Index`是將文件/檔案製作索引放入資料庫中。
- Import文件/檔案進入資料庫後，會佔有空間，當檔案損毀時，就無法再救出來了。
- Index並不會增大你的資料庫，且當資料庫檔案有損毀時，原檔並不會消失。
- 好像Index比Import還安全，但，其實資料庫並非這麼容易損毀(最少我沒遇過)。
- Import的好處是，可以將資料庫檔直接放入隨身碟，往後你的所有資料就在這之中，可以隨易攜帶。且備份就只要備份這一個檔案，就全備份完畢，這是Index所做不到的。

要選擇哪一種方式，就看您自己的需求去決定。這沒有絕對的標準答案。

> 我的方式是，一般文件/檔案我全都用Import的方式。但是對於語音檔、影片、照片等，非常佔容量的檔案用Index。

## 先決定文件要存在哪

### 一.放入Inbox中

在系統設定內，選擇Import的頁籤可以看到相關的設定。

![](http://i.imgur.com/LK72pXt.png)

系統在GLOBALS有預設的Inbox，這Inbox是出現在Finder的側邊欄位，一般而言假如透過掃描器的文件檔、網站的截取、相關的Scripts所匯入的檔案、或者是拖拉放方式丟到Inbox的資料，都會先放到`GLOBAL`->`Inbox`中。

![Finder中的Inbox](http://i.imgur.com/5TTGglA.png)

圖中所示即是Finder中的Inbox資料夾，將檔案放在這裡，會自動被丟到Global的Inbox中。因為資料都自動被移走，所以這裡是_看不到檔案_的。

### 二.放入指定的資料夾

假如是在開啟DEVONthink的狀況下，也可以直接拖拉放的方式直接將檔案放入指定的資料夾。所以這是相當自由的。

![](http://i.imgur.com/4CK1ZTO.png)

之前有提到的`Groups & Tags`視窗，也適合用來拖拉放檔案。

> 假如找不到剛才自己放的檔案，建議先看看Global Inbox的group。若是找不到，可以看一下`Tools`->`History`->`Database Name`來找一下剛剛匯入的位置。

## 選一還是選二呢?

這也是沒有對與錯的事，端看你的個人習慣。以GTD為出發點，建議用第一個方式，將資料先放入Inbox之中，往後再Review這些相關的檔案，再做分類的工作。

選二的缺點是會打斷現行的思序，但已經先做好資料夾的管理，所以未來就可以不用花時間處理。

> 我的習慣是選一，都先放入Inbox之中，一個星期會整理一次資料，順便Rwview文件。這議題已經在思考GTD的運作，建議可以參考網路上相關的文章，先建立起自己的模式。不論選哪一種模式，DEVONthink都可以做得到。以下文章會說明更多的匯入方式，可以提供個人使用上的參考。

## 利用DEVONthink建立文件

![](http://i.imgur.com/VyV8Yzn.png)

在`Data`->`New`中，可以看到以上幾種可以建立的資料型態，以下作個簡單的說明。

- `With Clipboard`是直接新增現在系統簡貼簿中的文字。
- `Plain Text`新增純文字檔案，至於什麼是存文字，請自行Google。[Wiki](https://en.wikipedia.org/wiki/Plain_text)說明。
- `Rich Text`這也是自行Google的項目。[Wiki](https://zh.wikipedia.org/wiki/RTF)說明。
- `Formatted Note`通常從截取下來的網頁，都是屬於這檔案類型。是可以被編輯的。
- `HTML Page`這不用說明了吧，就HTML頁面。
- `Markdown Text`副檔名為.md檔，就是大家耳聞的Markdown檔案，在撰寫時是Markdown原檔，觀看時可以利用右上方`Best Alternative`按鈕切換成被編譯後的閱讀模式。
- `Sheet`要先輸入Column的參數，如下圖。

![](http://i.imgur.com/4dwrEK7.png)

然後就能產生像Excel一樣的資料表，如何應用，請自行先想像。

![](http://i.imgur.com/agYUbQ6.png)

可以透過按`New Record`的方式來新增資料。

- `Bookmark`DEVONthink是可以輸入Bookmark型式的資料，可以將Safari、Chrome、Firefox的Bookmark檔保存下來，直接點選連結，可以用內建的瀏覽器觀看網頁。
- `Feed`在網路上所看到的RSS連結，可以由此輸入，支援OPML、RSS等常見的Feed格式。
- `New From Template`這能真的很方便，可以將常輸入的文件，先建立一份Template檔，未來直接用這方式來撰寫。

![](http://i.imgur.com/uRtQaM5.png)

這示範一份日常的電話紀錄，時間會自動被記下來，不用再手動方式輸入。

範本可以是任何型式的檔案，未來只要將檔案放進範本資料夾中，就可以從這裡被引用新增。

## 托拉放 Drag and Drop

檔案或文件可以透過施拉放的方式，將資料Import進資料庫。可以拉到的地方包括:

- Dock Icon，直接拉到Dock上的DEVONthink程式，就可以自動匯入inbox之中。
- Group或Tag，拉到所想要放的位置也會被匯入。
- Group&Tags Panel，假如你有打開這面版，也是會被匯入指定的位置。
- DEVONthink Window，這就是直接拉到該View的視窗中。
- Global Inbox，這就是前面所說在Finder中的Inbox資料夾。在此說明一下特點。
  - 前述的四種方式，被拖拉放之後是被Copy一份資料，原檔案持續存在著。而放在Finder Inbox中算是被移動到Inbox中，所以原檔案會消失。
  - 拖到Global Inbox中，默認為放到主資料庫Inbox中，沒有如前四項有指定位置。
  - 這是一種GTD的概念，先將文件存下來，日後再做管理的動作，將相同的事情同時執行，就是GTD的實踐。

## Services Menu

在MacOS 10.6 Snow Lepard之後，提供了Service的方式，可以利用一些簡單的Scripts來達成複雜的工作。就如在Finder之中就可以找到Service的例子。如下圖:

![](http://i.imgur.com/xj2UjmY.png)

當灌好DEVONthink之後，就已經自動將這功能寫入到服務選單之中。

## Sorter

接下來說明一個令人又愛又恨的功能，有些人很愛，有些人卻又對這東西很反感。

在你的桌面上有一個常註的面版，可以隨易移動位置，可以任意放不同的資料夾作預設。

![](http://i.imgur.com/jphXpdj.png)

我的習慣是把正在處理中的資料夾放入插槽中，當找到相關的資料，可以直接拖拉放至這裡，然後就會被放到指定的資料夾中。

使用情境比如正在寫論文，可以在網路上找到的資料，一股腦兒全放到論文資料夾中，未來就可以統一做整理。但有些人覺得這東西一直常註在桌面上很礙眼，所以如何應用，端看個人的使用習慣決定。

## Bookmarklets

在[這裡](http://www.devon-technologies.com/download/extras.html)可以找到DEVONthink的相關外掛，你可以將Bookmarklets直接拉到書籤之中，當未來找到想要存的網站資料，可以利用這方式直接將網頁存成想要的格式。現在有以下幾種格式可以選擇:

- Clip to DEVONthink
- Archive
- Bookmark
- HTML
- PDF
- PDF(paginated)
- Selection
- Text

把這幾項集合成一個Bookmarklet資料夾，點選執行，也是很簡單的一種做法。

![](http://i.imgur.com/3422B9V.png)

## 從Email內新增

DEVONthink Pro版以上，可以直接與Apple Mail做整合。好處是:

- 將專案文件一起存放。
- 利用DEVONthink來整理專案檔案，也可以使用See Also、Tag、Replicant的方式管理email的訊息。
- 最大的好處是，DEVONthink真的運算很快且有彈性，在搜尋上可以很快的找到自己要的檔案。

![](http://i.imgur.com/cR4bfhT.png)

DEVONthink支援Apple Mail、Microsoft Outlook、Unix Mailbox等三種信箱。不過我已經轉到Airmail使用已經太久了，所以這部份我幾乎都不是用此方式操作。至於如何用Airmail來匯入，因這不是內建的主要服務，未來再找時間說明。

## 利用PDF選單

![](http://i.imgur.com/12RnTG6.png)

在預設的列印功能中，左下角會有PDF字樣，可以利用已經自動幫你設好的PDF Scripts將文件直接輸出成PDF檔，並放入DEVONthink之中。

圖中因為我有灌個人版與Pro版兩種(試用)，所以會出現兩個Scripts。若只有裝過一種DEVONthink，就不會與我相同的呈現畫面。

> 可以應用在Safari列印網頁時，選擇網印網站，將網站存成PDF檔，並置入DEVONthink之中。好處是保留了網站原本的排版模式，所以若有這方面的需求，可以選擇此方法輸入。

## 利用內建瀏覽器

DEVONthink已內建與Safari相同的WebKit引擎，所以用內建的瀏覽器，理論上所看到的與Safari是完全相同。一樣可以用來截取網頁，可以選擇適合的格式存放，如Plain text、Rich text、Formated Note、或是直接存成HTML檔。

因為操作方式太直覺了，我就懶得介紹啦。

## 利用RSS Feeds

![](http://i.imgur.com/CNB6Ijv.png)

DEVONthink內建RSS訂閱器，透過`Data`->`New`->`Feed`可以開啟對話視窗。你只要將Feed放入，往後就會開始訂閱。

![](http://i.imgur.com/Z74rPdJ.png)

相關Feed的設定，可以在`Preference`找以找到設定參數。

- Check for update: 檢索的時間差，可以隨自己喜愛設定時間。
- Skip duplicates: 因為很多Feed可能都是轉貼相同的來源，DEVONthink很聰明的，可以命令他判斷相同的文件。如此在讀到相同的文章時，會自動捨棄掉。
- Convert categories to tags: 這不用說明了，就Tags會自動包含group的性質。
- Remove articles: 這假如不選，資料就會一直被截取出來且存在資料庫中，除非自己刪除，不然不會消失。可以隨自己喜愛的方式去設定。
- Also unread articles: 自動刪除時，會不會也刪除掉未讀的文章，預設是關閉。
- Feed Style Sheet: 選擇不同的CSS去格式化你的Feed，一般選Default.css即可，除非有特別需求，不然不用動這一項。

> 我會習慣有興趣的Feed文章，直接拖拉放至Inbox中，這可以很方便做歸檔的動作。剩下文章就不去理他，於指定的時間就會自動被丟到垃圾筒中。

## 結語

零零總總寫了這麼多的方式做檔案/文件的輸入，最大的心得就是，DEVONthink根本就是個垃圾筒，不論何種方式都有辦法把檔案置入。有時甚至比內建的垃圾筒還要不挑檔案。

我把DEVONthink定義為我的Data Warehouse，把所有的文件都放置於此，利用程式快速的搜尋功能，快速的建立我的個人知識資料庫。

接下來將說明的是如何管理這個資料庫。
