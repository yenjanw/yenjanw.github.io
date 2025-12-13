+++
title = 'DEVONthink(二)'
subtitle = '操作介面'
date = '2017-04-20T17:35:50+08:00'
draft = true
tags = ['文件管理']
categories = ['DEVONthink']
+++

初裝好DEVONthink打開一看，哇!這應該算上個十年才有的操作介面吧，但是細細的往內一看，所有的功能一項都不缺，有些就隱藏在小小的角落，不讓你發現，這只有德國人才想得出的設計風格。假如你願意奈住性子，先不從外觀評論一個軟體，慢慢的去了解這它對你的幫助有多麼的巨大，未來的脫離不開了。

以下說明都是以DEVONthink Pro Office 2.9.6作為說明的版本，若畫面或操作介面不相同，應是版本的差異所致。

<!-- more -->

## 主視窗

一開啟程式，就可以看到這主要的視窗介面。

![](http://i.imgur.com/nqAsQcs.png)

這畫面分成三個部份，上方的Toolbar、左邊的Sidebar、中央一大區塊為Views。

## Toolbar

![](http://i.imgur.com/Vt1iIZ7.png)

這裡可以讓你找到快速按鈕，讓您切換畫面或是快速的建立文件與分類。

![](http://i.imgur.com/KKd8XBP.png)

要更改可以從`View`->`Customize Toolbar`利用對話窗來拖拉放你要的東西，操作很像之前iWorks的方式，相當直覺。

## Sidebar

![](http://i.imgur.com/ozOozsv.png)

這區塊是分類的快速點選區，有分成Globals、Open Database、Recent Database、Favorites與Smart Groups，前三項是Database的分類，後兩項是Groups。

> 注意: 多個Database只在DEVONthink Professional版以上才有，若是使用DEVONthink Personal版只會有一個資料庫而已。

假如覺得這區塊很礙眼，可以從`View`->`Hide Sidebar`把它關閉。

## Views

![](http://i.imgur.com/vt0P6vz.png)

在 Toolbar中有個可以切換View的選項按鈕，在DEVONthink中有六種瀏覽方式。前三項(Icon View、List View、Column View)很像Finder的方式。後三項(Split View、Three Pane View、Tag View)的方式，可以用另一種思維去看檔案，以獲得更多的資訊。

### Icon View (⌘1)

![](http://i.imgur.com/it9Zet9.png)

是不是很像Finder一樣啊?右上方還有拉Bar可以控制圖的大小，當檔案真的很多的時候，大小控制適當就很重要了。

> 檔案的排序可以從`View`->`Sort`的底下去找，一般而言都是用名字排序，若有其他需求都可以從那去控制。

### List View (⌘2)

![](http://i.imgur.com/8voZJ8F.png)

預設會顯示Name、Modified、Kind、Size與URL，若要更改，可以在上面按右鍵來選取，當然大小也可以用拉的來調整。

### Column View (⌘3)

![](http://i.imgur.com/C4MlCt9.png)

這模式可以一直往下挖資料夾。上圖是只顯示三層而已，若資料很深，可以一直往下挖，個人最深是放到七層，試過沒有問題。

> 官方的資料顯示，可以無限制的往下挖。

下半部是你現在所處位置的Icon View，最下面一排還有**Tag**顯示(可以用`⌃⌥⌘T`來開啟或關閉)。

這部份的排列一樣是從`View`->`Sort`的方式去設定。

### Split View (⌘4)

![](http://i.imgur.com/1jBWKA5.png)

分割視窗包含垂直的的Group列表與文件，在`Widescreen`模式下，右方還預設顯示文章內容。

### Three Pane View (⌘5)

![](http://i.imgur.com/sq4MfnD.png)

這有點像是Split View，將文件用List的方式呈現，並且在下方顯示文件內容。若是在`Widescreen`模式下，文件內容會顯示在右方。

### Tag View (⌘6)

![](http://i.imgur.com/lAikCSQ.png)

最後是Tag View，完全是以Tag的角度出發思考的設計介面，右方顯示資料庫內(**現在所屬的資料庫**)所有的Tag，點選後在左方顯示內容。完全打破Group的概念，只把相關的Tag拉出。

所以前五項是以Group的角度去思考，最後一項是用Tag的角度去思考。至於何時要何種介面，這是有個人習慣的考量。現在內容尚屬於介紹的層級，我就先不去給各位先入為主的觀念，自己先去摸索是很重要的。

### Navigation Bar

![](http://i.imgur.com/h1JpEec.png)

在每一個編輯視窗，都會出現如上圖的導覽Bar，從左至右分別為上一頁、下一頁、網址、文章資訊、Reload、鎖定、前一個Highlight、後一個Highlight、文字分析(word)、See also與Classify、關鍵字、Tag Bar。

這部份之後會列專文說明各個的用途，先了解有這些東西就好。

# 顯示選項

除了六個主視窗View的方式外，DEVONthink還有幾個不同的不同的顯示選項可以使用。以下介紹都加上快速鍵，可以自行開啟與關閉。

## Cover Flow (⌥⌘O)

![](http://i.imgur.com/aOuOgSn.png)

利用Mac本身的Cover Flow功能來顯示文件，多是用在顯示圖片的功能上，假如是顯示一般文件，也只有文件的縮圖，就如同Mac本身的功能相同。

這種顯示方式只能用在**Column、Split、Three Pane、Tag**等模式上。

## Tags (⌃⌥⌘T)

![](http://i.imgur.com/2cqq5GR.png)

在文件的下方，會有Tags的顯示區域，可以直接點選更改成類似的Tag，或是在後面新增Tag的分類。

DEVONthink會自動將Group加到Tags之中。假如是屬於Group的Tag，呈現**灰色**，若是不屬於Group的則呈現**藍色**。

## Details (⌥⌘L)

![](http://i.imgur.com/PPHPSKs.png)

只能用在Icon View模式，顯示更多的內容與資訊，這樣使得Icon View獲得如同List View的功能一樣。

## Widescreen (⌥⌘W)

只能用在Split View與Three Pane View上，讓內容顯示在右側而非下方。預設是關閉的。因我的電腦畫面不夠寬，所以開啟不了這功能。就不再作截圖示範了。

## Full Screen

全螢幕有兩種模式，一個是針對視窗的全螢幕(⌃⌘F)，另一種是針對文件的全螢幕(⌘F7)。

![](http://i.imgur.com/wykSyhI.png)

就如同Mac 10.11之後的全螢幕模式一般，把整個視窗填滿。

![](http://i.imgur.com/rYjIfXy.png)

只有文件顯示的部份填滿視窗，還蠻方便的，可以使所有的干擾都消除，達到Focus的效果。

# 面版 Panels

部份的視窗功能，在DEVONthink之中被稱作`Panels`，與一般的視窗功能上有一點點不太相同，通常可以提供一些特殊的功能，或者是額外的資訊。這些面版是相對於主視窗獨立而生的，不會依附著。以下就是一些特殊的面版介紹。

## Information (⌘⇧I)

![](http://i.imgur.com/Epj9cQb.png)

可以從`Tools`->`Show info`把它叫出來，有著文件的基本資訊。這些資訊也都可以修改的，未來會再詳述這些部份。

## Properties (⌘⌥⇧P)

![](http://i.imgur.com/oJH3sOI.png)

可以從`Tools`->`Show Properties`把它叫出來，這與一般的視窗也點不同，他是黑色且透明的。這裡可以輸入一些文件的meta data。

## Groups & Tags(⌘⌃G)

![](http://i.imgur.com/4CK1ZTO.png)

可以從`Tools`->`Show Group & Tags`把它叫出來，這裡擁有資料庫內所有的Group。有時候文件很多時，要做分類我習慣把這面版叫出來，直接用拖拉放的方式將文件移動位置。直接點選兩下，也可以顯示該Group視窗。

## Download Manager(⌘⌃L)

![](http://i.imgur.com/tKEHTjv.png)

可以從`Window`->`Download Manager`把它叫出來，當有下載時候，可以看出來這些動作。通常是利用DEVONthink內建的瀏覽器讀取網頁時，才會有下載的動作。這與Safari或是Firefox的運作原理相同。

## Log

![](http://i.imgur.com/QyhBMbi.png)

可以從`Window`->`Log`把它叫出來，當有發生需要你注意的項目時，這畫面會自行跳出來警告你。之前我曾把DEVONthink的data base檔案放在Google Drive同步的資料夾下，就一天到晚警告我這樣是不好的，一定要移離開該位置。

## History

![](http://i.imgur.com/XekYFNS.png)

這面版可以看到資料庫的運作過程，如上圖，這是近期運作的紀錄，資料庫寫入了很多的RSS資料。每次你新增或刪除資料的紀錄都會存放在這裡。

## 抽屜 Drawers

有一些視窗，它是依附著主視窗而生，這些在DEVONthink被稱作`Drawers`，下方就簡單說明一下。

## See Also & Classify(⌘⌃S)

![](http://i.imgur.com/dm4XcDh.png)

可以從`Data`->`See Also & Classify`把它叫出來，這是DEVONthink主要的功能之一，在See Also中，DEVONthink透過特殊的演算方式，找出相關的文章，這幾乎可以當作個人版的Wiki來使用了。

而上方的是建議的Group，也是透過演算法建議有哪些Group適合這篇文章來放。

> 官方網站說明這功能有人工智慧(AI)的能力，我還在慢慢訓練我的DEVONthink，看是否會越來越準確。

## Concordance

![](http://i.imgur.com/PmLehYA.png)

這個Drawer是計算著這文章中，相同的字句出現的次數，與字句的長度寬度。個人認為這部份以英文運作是很好的，但中文部份斷句還是不夠精確(~~根本不及格~~)。

> 這功能要在DEVONthink Professional版以上才有。

## Document Windows

![](http://i.imgur.com/yKacSa2.png)

大部份在DEVONthink的文章，點選兩下就可以出現這一個視窗，可以用來編輯與修改文章的內容。假如只是要快速的查看內容的話，建議可以按一下`空白鍵`來`Quick Look`就可以了。

假如是新增文章的話，是透過`Data`->`New`的方式，選擇要新增的文章格式。在DEVONthink中支援多種文件格式，最重要的是可以支援`Markdown`，這點對我來說非常重要。這部份內容未來也會再詳述。

## 結語

有沒有覺得這軟體功能真的很強大，居然零零總總的細項功能這麼得多，很多小細節都有顧到。這也是我推薦的原因。

說明到現在，其實都還沒有將資料放到Database之中，所以內容還不算真正的開始呢(什麼?)。

真的，DEVONthink真的很強大，強大到不知從何處起筆。從操作介面算是一個開始，而不是結束。慢慢得我會再新增一些近日使用上的心得，希望對已經在使用或是正在評估中的使用者有幫助。