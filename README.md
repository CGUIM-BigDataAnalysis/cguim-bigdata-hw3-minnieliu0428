長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Loading required package: xml2

``` r
pptUML1 <- "https://www.ptt.cc/bbs/Tech_Job/index2571.html"
pptUML2 <- "https://www.ptt.cc/bbs/Tech_Job/index2572.html"
pptUML3 <- "https://www.ptt.cc/bbs/Tech_Job/index2573.html"
pptUML4 <- "https://www.ptt.cc/bbs/Tech_Job/index2574.html"
pptUML5 <- "https://www.ptt.cc/bbs/Tech_Job/index2575.html"

b <- c(pptUML1, pptUML2, pptUML3, pptUML4, pptUML5)
frameALL <- NULL

for(n in b){
pptTJ <- read_html(n)
title <- pptTJ %>%
html_nodes(".title") %>%
html_text()
pushNum <- pptTJ %>%
html_nodes(".nrec") %>%
html_text()
author <- pptTJ %>%
html_nodes(".author") %>%
html_text()
frame <- data.frame(Title = title, PushNum = pushNum, Author = author)
frameALL <- rbind(frameALL, frame)
}
```

爬蟲結果呈現
------------

``` r
knitr::kable(frameALL) ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| Title                                                            | PushNum | Author       |
|:-----------------------------------------------------------------|:--------|:-------------|
| \[請益\] 系統廠or ic廠QA                                         | 4       | skycoolguy   |
| \[心得\] VIS/THSR/TSMC/友達/美光                                 | 21      | lani0529     |
| \[新聞\] 台廠風光不再！中國IC設計廠翻倍台灣僅微                  | 13      | BBMADE       |
| Re: \[討論\] 公司特休尚未給                                      | 11      | simonho      |
| \[徵才\] NCTU x TSMC 徵博士後研究員1名                           | 23      | kk74en       |
| \[請益\] 輪班助工vs 夜班OP                                       | 8       | followth     |
| Re: \[新聞\] 台廠風光不再！中國IC設計廠翻倍台灣僅微              | 5       | SMIC5566     |
| \[新聞\] 股王離職員工爆被要求歸還紅利　大立光這                  | 19      | kof70380     |
| Re: \[心得\] 南u製程工作心得                                     |         | livefishfish |
| \[徵才\] 日本最大獨角獸－mercari 台灣徵才                        |         | TOPCAREER    |
| Fw: \[情報\] 清大校園徵才週六開跑！                              | 2       | swkai8497    |
| \[面試\]佳凌/穩懋/包子/乾坤/gg/新唐/艾克爾                       | 13      | nick65415    |
| \[請益\] 有沒有FMEA界霸主 UMCi林x良顧問的掛？                    | 15      | qoo78918     |
| Re: \[心得\] 南u製程工作心得                                     | 爆      | BLF          |
| Re: \[討論\] 31歲轉換跑道還來的及嗎                              | 2       | GuitarOcean  |
| \[心得\] 好像這樣                                                | 1       | agv88        |
| Re: \[討論\] 參考人怎麼填?                                       | 20      | NaClman      |
| Re: \[新聞\] 聯發科員工分紅 連二年下滑                           | 11      | sszaq        |
| \[請益\] 奧璐佳瑙                                                | 1       | peacesea     |
| \[新聞\] 夏普將買群創面板 明年電視要賣1000萬台                   | 7       | cymei113     |
| \[請益\] 另一半認為, 7:00下班是不顧家庭                          | 99      | AK47shoot    |
| \[討論\] 遇到這種主管怎麼辦                                      | 18      | sustaned     |
| \[心得\] 聯發科年薪 VS GG年薪                                    | 37      | irishcafee   |
| \[新聞\] 台灣IC設計全球第2 僅次於美國                            | 7       | sb5471       |
| (已被mmkntust刪除) <x20911> 版規六                               |         | -            |
| \[請益\] 台達電薪資請益                                          | 13      | TC5566       |
| \[請益\] 戀人通知等待時間                                        | 17      | chemical1223 |
| \[情報\] 106年IC layout人才養成班 (代PO)                         | 4       | katykk       |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 16      | head109      |
| \[請益\] 資訊維修or設備安裝                                      | 7       | jimmy357     |
| Re: \[討論\] 遇到這種主管怎麼辦                                  | 2       | maxgxking    |
| \[討論\] 誰決定面試者來面試                                      | 7       | magic704226  |
| \[討論\] 2011年在HTC的員工 現在都跳哪了？                        | 46      | hosadavid    |
| Re: \[討論\] 遇到這種主管怎麼辦                                  | 6       | damm         |
| \[請益\] 台橡化工技術員面試一職                                  |         | minwoo0904   |
| \[請益\] 台塑宜蘭廠                                              | 9       | nerlens      |
| \[請益\] acer system engineer                                    |         | ccc0901      |
| Re: \[心得\] 南u製程工作心得                                     | XX      | livefishfish |
| \[面試\] 台積設備/應材客服/南亞科設備 請益                       | 9       | s50190       |
| Re: \[情報\] 106年IC layout人才養成班 (代PO)                     | 9       | SUPER22K     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 18      | Feases       |
| (本文已被刪除) \[wer11\]                                         |         | -            |
| \[心得\] 船舶暨海洋產業研發中心 面試心得                         | 14      | kevin505     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 47      | cjb          |
| \[請益\] 科技部工作經歷在Linkedin上的名稱                        | 1       | Paravion     |
| Re: \[新聞\] 海邊台大校園徵才圓滿落幕　收穫逾2000履歷表          | 31      | LibertyWings |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 7       | zxlu         |
| \[討論\] 程式語言筆試面試的準備                                  | 1       | magic704226  |
| \[心得\] 海邊面試的搞笑經驗                                      | 19      | tw689        |
| \[請益\] 大公司的話 個資可以放心填?                              |         | jason050117  |
| \[請益\] OFFER選擇 (群創光電V.S台電機械職員                      | 53      | Moran        |
| \[請益\] 請問螃蟹的Android/Media軟體設計工程師                   | 1       | magic704226  |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 爆      | AK47shoot    |
| (本文已被刪除) \[ck960164\]                                      |         | -            |
| \[請益\] 大立光物管工程師                                        | 14      | omes4219     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 42      | TSMCer       |
| \[徵才\] EasyStack徵才年薪120萬台幣起                            | 10      | mimi0213     |
| (本文已被刪除) \[iamp\]                                          | 19      | -            |
| (本文已被刪除) \[zx212012\]                                      | 13      | -            |
| \[請益\] 請教大碩面試後等通知需要等多久？                        | 19      | uasalada     |
| Re: \[請益\] OFFER選擇 (群創光電V.S.台電機械職                   | 18      | lsz6404      |
| \[請益\] 台積電 EMITD 工作內容                                   | 19      | innocentguy  |
| \[新聞\] ic設計每股獲利洗牌 聯發科跌落3名外                      | 20      | LBJ2ndKing   |
| (本文已被刪除) \[seei\]                                          | 4       | -            |
| \[請益\] 住華 新技術開發 and 奇美材 製程 詢問                    | 4       | Edwardkiller |
| \[請益\] 研替offer(京元/緯創）                                   | 7       | starjli      |
| \[請益\] 碩一暑期實習                                            | 4       | a29417557    |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 5       | HateAnus     |
| (本文已被刪除) \[Federer56\]                                     | 6       | -            |
| \[請益\] 水果公司的工廠，工程師好跳嗎？                          | 15      | ggggggh      |
| \[面試\] 化工面試 住友/三井/花王/景碩/陶麗西/新光/清錄/麥特/艾克 | 55      | BCCAT        |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 28      | unclefucka   |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 1       | cacalota     |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 17      | jessicabana  |
| (本文已被刪除) \[Nippey\]                                        | X1      | -            |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 19      | soufon       |
| (本文已被刪除) \[darkcurrent\]                                   |         | -            |
| \[心得\] 小公司的慎選...                                         |         | JT0816       |
| \[閒聊\] 海邊的一盤大棋                                          | 23      | balzark      |
| (本文已被刪除) \[HAAH\]                                          |         | -            |
| Re: \[請益\] 另一半認為, 7:00下班是不顧家庭                      | 31      | smallchou    |
| \[請益\] 請問應徵台積OP是否有黑名單                              | 35      | kn0105209    |
| \[新聞\] 郭台銘：陸大學生動手能力差                              | 21      | BBMADE       |
| Re: \[新聞\] 郭台銘：陸大學生動手能力差                          |         | schizophrena |
| \[新聞\] 斥資600億 「綠能科學城」落腳台南沙崙                    | 21      | hottea88310  |
| (本文已被刪除) \[ffelix1202tw\]                                  |         | -            |
| 滷肉開獎                                                         | 46      | crafttt      |
| \[新聞\] 台積電3奈米廠出走？傳5000億落腳美國                     | 49      | popoallan    |
| Re: \[新聞\] 台積電3奈米廠出走？傳5000億落腳美國                 | 5       | appledavid   |
| \[新聞\] 台積電成環評箭靶　網友酸農地工廠卻就                    | 26      | wahaha23     |
| \[面試\] 中華精測目檢檢驗工程師                                  | 3       | poiipkimo    |
| Fw: \[新聞\] 新世代最崇拜企業家　郭董取代賈柏斯                  | X3      | tw689        |
| \[請益\] 工作上想成長,想上點課程~                                | 6       | kevinZJL     |
| Re:Sex5F (101.139.108.163), 03/20/2017 12:47:                    | 1       | Sex5F        |
| \[請益\] 伺服器發展性與基本概念問題                              | 7       | ScrewYou     |
| (本文已被刪除) \[ffelix1202tw\]                                  |         | -            |
| \[請益\] 研替or一般替代役                                        | 26      | charisma007  |
| \[請益\] 達運光電(五股)                                          | 1       | smst         |
| \[情報\] 106年03月22日\_竹科\_IC設計產業座談會                   | 1       | SuperModel   |
| Re: \[請益\] 點序科技業務職面試請益                              |         | hueepf       |

解釋爬蟲結果
------------

``` r
nrow(frameALL)
```

    ## [1] 100

總共爬出100篇文章標題。

``` r
sort(table(frameALL$Author))
```

    ## 
    ##        agv88          BLF     cymei113     followth  GuitarOcean 
    ##            1            1            1            1            1 
    ##       kk74en     kof70380     lani0529      NaClman    nick65415 
    ##            1            1            1            1            1 
    ##     peacesea     qoo78918      simonho   skycoolguy     SMIC5566 
    ##            1            1            1            1            1 
    ##        sszaq    swkai8497    TOPCAREER      ccc0901 chemical1223 
    ##            1            1            1            1            1 
    ##         damm      head109    hosadavid   irishcafee     jimmy357 
    ##            1            1            1            1            1 
    ##       katykk    maxgxking   minwoo0904      nerlens       s50190 
    ##            1            1            1            1            1 
    ##       sb5471     SUPER22K     sustaned       TC5566          cjb 
    ##            1            1            1            1            1 
    ##       Feases  jason050117     kevin505 LibertyWings     mimi0213 
    ##            1            1            1            1            1 
    ##        Moran     omes4219     Paravion       TSMCer     uasalada 
    ##            1            1            1            1            1 
    ##         zxlu    a29417557      balzark        BCCAT     cacalota 
    ##            1            1            1            1            1 
    ## Edwardkiller      ggggggh     HateAnus  innocentguy  jessicabana 
    ##            1            1            1            1            1 
    ##       JT0816   LBJ2ndKing      lsz6404       soufon      starjli 
    ##            1            1            1            1            1 
    ##   unclefucka   appledavid  charisma007      crafttt  hottea88310 
    ##            1            1            1            1            1 
    ##       hueepf     kevinZJL    kn0105209    poiipkimo    popoallan 
    ##            1            1            1            1            1 
    ## schizophrena     ScrewYou        Sex5F    smallchou         smst 
    ##            1            1            1            1            1 
    ##   SuperModel     wahaha23       BBMADE livefishfish    AK47shoot 
    ##            1            1            2            2            2 
    ##        tw689  magic704226            - 
    ##            2            3           12

在爬出的100篇文章當中，文章數最多的作者是magic704226，共有三篇文章。

-   ppt上面顯示被刪除的文章在Author會顯示-，可以知道包含幾篇被刪掉的文章。
-   可以使用mean()函數看看平均按讚數是多少。 mean(frameALL$PushNum)
-   利用subset()函數，可以找出被網友推爆的文章，進而知道網友對哪些文章比較有興趣。 subset(frameALL, PushNum =="爆")
-   可以知道哪些人的文章沒有人推文（Author不為-，且PushNum沒有數值）。
