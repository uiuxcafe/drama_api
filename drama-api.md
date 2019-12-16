<!-- TOC -->

- [1.列表](#1列表)
  - [1.1 輪播列表](#11-輪播列表)
    - [新聞](#新聞)
    - [戲劇](#戲劇)
  - [1.2 首頁列表](#12-首頁列表)
    - [新聞](#新聞-1)
    - [戲劇](#戲劇-1)
    - [討論](#討論)
  - [1.3 分集大綱列表](#13-分集大綱列表)
  - [1.4 熱門關鍵字列表](#14-熱門關鍵字列表)
  - [1.5 搜尋結果列表](#15-搜尋結果列表)
    - [關鍵字搜尋 | Tag 搜尋](#關鍵字搜尋--tag-搜尋)
    - [篩選搜尋](#篩選搜尋)
    - [相關結果搜尋](#相關結果搜尋)
- [2. 詳細](#2-詳細)
  - [2.1 首頁詳細頁](#21-首頁詳細頁)
    - [新聞](#新聞-2)
    - [戲劇](#戲劇-2)
  - [2.2 分集大綱詳細頁](#22-分集大綱詳細頁)

<!-- /TOC -->
# 1.列表
## 1.1 輪播列表

_進入新聞、戲劇首頁時，打此 api，即顯示輪播列表。不限內容數量，採用人工調整。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]
- 戲劇 WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]

### 新聞
- Query
 
```
    query {
       carosell (where: {type: {_eq: "news"}})
       {
          id
          title
          img
       }
    }

```
<!-- - mutation [新增] //不太確定如何打，如何加入帶入要新增的位置 news/drama?

```
    insert_carosell {
       {
          id: 6
          title: 閨蜜撕破臉！?,
          img: https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png,
       }
    }
    
```

- mutation [更新] //不太確定如何打

```
    update_carosell {
       {
          id: 6
          title: 閨蜜撕破臉！?,
          img: https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png,
       }
    }
    
```

- mutation [刪除] //不太確定如何打

```
    delete_carosell {
       {
          id: 6
          title: 閨蜜撕破臉！?,
          img: https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png,
       }
    }
``` -->

### 戲劇
- Query [戲劇]
 
```
    query {
       carosell (where: {type: {_eq: "drama"}})
       {
          id
          title
          img
       }
    }

```

- Server Response

```json
{ 
    "data": {
        "carosell":[
            {
            "id": 1,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

---

## 1.2 首頁列表
_進入新聞、戲劇、討論首頁時，打此 api，即顯示最新列表。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]
- 戲劇 WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]
- 討論 WF [https://whimsical.com/JFAQ65FCGBdjmua5EDxENp]


### 新聞
- Query
 
```
    query {
       news (limit: 10, order_by: {post_date: desc}, offset: 10)  // limit:一次取10筆，order_by:最新順序由上至下，offset: 取第10筆之後
       {
          id
          title
          date
          preview
          img
       }
    }

```

- Server Response

```json
{ 
    "data": {
        "news":[
            {
            "id": 1,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-23 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-20 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-19 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-12 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

### 戲劇
- Query
 
```
    query {
       drama (limit: 15, order_by: {post_date: desc}, offset: 15)  
       {
          id
          title
          img
       }
    }

```

- Server Response

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"抓住幽靈",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"那一天",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"忠孝節義路遙知馬力",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 15,
            "title":"還是不能結婚的男人",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```



### 討論 


- Query [美劇] 
 
```
    query {
       forum (where: {region: {_eq: "us"}}, limit: 10, order_by: {post_date: desc}, offset: 10) 
       {
          id
          title
          date
          source // 來源
          img
       }
    }

```
- Query [陸劇]
 
```
    query {
       forum (where: {region: {_eq: "china"}}, limit: 10, order_by: {post_date: desc}, offset: 10) 
       {
          id
          title
          date
          source // 來源
          img
       }
    }

```

- Query [韓劇]
 
```
    query {
       forum (where: {region: {_eq: "korea"}}, limit: 10, order_by: {post_date: desc}, offset: 10)
       {
          id
          title
          date
          source // 來源
          img
       }
    }

```

- Query [日劇]
 
```
    query {
       forum (where: {region: {_eq: "japan"}}, limit: 10, order_by: {post_date: desc}, offset: 10)  
       {
          id
          title
          date
          source // 來源
          img
       }
    }

```

- Query [台劇]
 
```
    query {
       forum (where: {region: {_eq: "taiwan"}}, limit: 10, order_by: {post_date: desc}, offset: 10) 
       {
          id
          title
          date
          source // 來源
          img
       }
    }

```

- Server Response

```json
{ 
    "data": {
        "forum":[
            {
            "id": 1,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-23 2:37:56",
            "source": "ptt",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-20 2:37:56",
            "source": "dcard",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-19 2:37:56",
            "source": "ptt",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-12 2:37:56",
            "source": "dcard",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

## 1.3 分集大綱列表
_進入戲劇詳細頁後，點選下方分頁「分集大綱」，即打此 api 顯示該劇分集大綱。_

<font color=#FFAA33>
Q:
1.按照集數排序應該如何寫？ 
</font>

- 分集大綱 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

- Query 
```
    query {
       drama (id: "1") 
       { 
           outline (limit: 10, order_by: {episode_number: desc}) 
            {
                id
                title
                episode // 集數
                preview // 預覽資訊
                img
            }
       }
    }

```


- Server Response

```json
{ 
    "data": {
        "outline":[
            {
            "id": 1,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"1",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"2",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"3",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 4,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"4",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 5,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"5",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 6,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"6",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 7,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"7",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 8,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"8",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 9,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"9",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 10,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"10",
            "preview":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        }        
        ]
    }
}
```

## 1.4 熱門關鍵字列表
_用戶點選搜尋後，打此 api ，即顯示近期熱門搜尋關鍵字，用戶可點選任一關鍵字進行搜尋。_

<font color=#FFAA33>

</font>

- 搜尋 WF [https://whimsical.com/6yDEHPB1YTN3Q8T9FU6Gop]

- query 

```
    query {
       hot  
       {
          id
          keyword
       }
    }
    
```

- Server Response

```json
{ 
    "data": {
        "hot":[
            {
            "id": 1,
            "keyword":"延禧攻略",
        },
        {
            "id": 2,
            "keyword":"2019",
        },
        {
            "id": 3,
            "keyword":"金所炫",
        },
        ...
        {
            "id": 10,
            "keyword":"延禧",
        },
        ]
    }
}
```

<!-- - mutation [新增] //不太確定如何打

```
    insert_hot {
       {
          id: 11,
          keyword: 2018
       }
    }
    
```

- mutation [更新] //不太確定如何打

```
    update_hot {
       {
          id: 11,
          keyword: 2018
       }
    }
    
```

- mutation [刪除] //不太確定如何打

```
    delete_hot {
       {
          id: 11,
          keyword: 2018
       }
    }
    
``` -->

## 1.5 搜尋結果列表
_當用戶透過輸入關鍵字、點選 Tag 搜尋戲劇相關資料，輸入完畢點選送出，即可打此 API。_

- 關鍵字/ Tag 搜尋 WF [https://whimsical.com/6yDEHPB1YTN3Q8T9FU6Gop]
- 篩選結果 WF [https://whimsical.com/4WBuD65bkGkLVhESwb4pY1]
- 相關結果 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]


### 關鍵字搜尋 | Tag 搜尋
_用戶直接在 search bar 關鍵字，點選送出，即可依據關鍵字顯示結果列表。_

_用戶點選新聞詳細頁的 Tag 後，即可打此 api，即可依據 Tag顯示結果列表。_


- query [新聞]
```
    query {
       news (where: {post_title: {_ilike: "%延禧%"}},limit: 10, order_by: {post_date: desc}, offest:10)  
       {
          id
          title
          date
          preview
          img
       }
    }

```

- Server Response [新聞]

```json
{ 
    "data": {
        "news":[
            {
            "id": 1,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-23 2:37:56",
            "preview": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-22 2:37:56",
            "preview": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-21 2:37:56",
            "preview": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-15 2:37:56",
            "preview": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

- query [戲劇]
```
    query {
       drama (where: {drama_title: {_ilike: "%延禧%"}},limit: 10, order_by: {post_date: desc}, offest:10)  
       {
          id
          title
          year
          actor
          img
       }
    }

```

- Server Response [戲劇]

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"延禧攻略",
            "year": "2019-05-23 2:37:56",
            "actor": ["鄭家藍","金所泫"],
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"延禧",
            "year": "2019-05-23 2:37:56",
            "actor": ["鄭家藍","金所泫"],
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"延禧攻",
            "year": "2019-05-23 2:37:56",
            "actor": ["鄭家藍","金所泫"],
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"延禧攻略x略",
            "year": "2019-05-23 2:37:56",
            "actor": ["鄭家藍","金所泫"],
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

- query [討論]
```
    query {
       forum (where: {forum_title: {_ilike: "%延禧%"}},limit: 10, order_by: {post_date: desc}, offest:10)  
       {
          id
          title
          source
          img
       }
    }

```

- Server Response [討論]

```json
{ 
    "data": {
        "forum":[
            {
            "id": 1,
            "title":"[情報] XXX 有望演出《延禧攻略》",
            "source": "PTT",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"#討論 延禧攻略 皇上 v.s. 傅恆",
            "source": "PTT",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"[心得] 出不了坑的延禧攻略 (有雷)",
            "source": "Dcard",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"[心得] 出不了坑的延禧攻略 (有雷)",
            "source": "PTT",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

### 篩選搜尋
_用戶在戲劇區時，可選擇以類型、地區進行篩選相關戲劇，篩選完畢即可打此 api，更新戲劇列表資料。_

<font color=#FFAA33>
Q:
//複選的表示方法？用 "","" 分開表示嗎？
</font>

- query [類別] 

```
    query {
       drama (where: {type: {_ilike: "%愛情%","%劇情%"}},limit: 15, order_by: {post_date: desc}, offest:15)  
       {
          id
          title
          img
       }
    }

```

- query [地區]
```
    query {
       drama (where: {region: {_ilike: "%美劇%"}},limit: 15, order_by: {post_date: desc}, offest:15)  
       {
          id
          title
          img
       }
    }

```

- Server Response 

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"喜歡的話請響鈴",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"喜歡的話請響鈴",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"喜歡的話請響鈴",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ...
        {
            "id": 15,
            "title":"喜歡的話請響鈴",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

### 相關結果搜尋
_當用戶進入新聞、戲劇詳細頁時，打此 api 下方會顯示相關新聞、戲劇、討論結果列表。_


- query [相關新聞]
```
    query {
       news (where: {post_title: {_ilike: "%綠豆傳%"}},limit: 3, order_by: {post_date: desc})  
       {
          id
          title
          date
          preview
          img
       }
    }

```
- Server Response [相關新聞]
  
```json
{ 
    "data": {
        "news":[
            {
            "id": 1,
            "title":"綠豆傳撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-23 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"閨蜜撕破臉！綠豆傳到底發生過什麼恩怨?",
            "date": "2019-05-20 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨綠豆傳?",
            "date": "2019-05-19 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```






- query [相關戲劇]
```
    query {
       drama (where: {drama_title: {_ilike: "%綠豆傳%"}},limit: 3, order_by: {post_date: desc})  
       {
          id
          title
          year
          actor
          img
       }
    }

```

- Server Response [相關戲劇]

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title": "抓住幽靈",
            "year": "2019",
            "actor": ["金所炫","張東尹"],
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"那一天",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"忠孝節義路遙知馬力",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        }
        ]
    }
}
```

- query [相關討論]
```
    query {
       forum (where: {forum_title: {_ilike: "%九%"}},limit: 3, order_by: {post_date: desc}) 
       {
          id
          title
          source
          img
       }
    }
    
```

- Server Response [相關討論]

```json
{ 
    "data": {
        "forum":[
            {
            "id": 1,
            "title":"[情報] XXX 有望演出《延禧攻略》",
            "source": "PTT",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"#討論 延禧攻略 皇上 v.s. 傅恆",
            "source": "PTT",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"[心得] 出不了坑的延禧攻略 (有雷)",
            "source": "Dcard",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```


---

# 2. 詳細
## 2.1 首頁詳細頁
_點選新聞、戲劇首頁任一新聞、戲劇後，打此 api，即取得該篇新聞、戲劇詳細資料。_ 

- 新聞 WF [https://whimsical.com/6peTte9KXein4Za26dMfTQ]
- 戲劇 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]
- 分集大綱 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

### 新聞

- Query 
  
```
    query {
       news (id: "1")
       {
          title
          date
          content
          img
       }
    }
```

- Server Response 

```json
{ 
    "data": {
        "news":[
            {
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-23 2:37:56",
            "content": "<p>內容</p><img src=“url/abc.png” alt=“”/>",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```

### 戲劇
_有預告link 先顯示預告，沒有 預告link 則顯示封面img。_

- Query
 
```
    query {
        
       drama (id: "1")
       {
            title
            content
            episode
            region
            year
            type
            actor         
            img
            video
        }
       }
```

- Server Response [有預告 link]

```json
{ 
    "data": {
        "drama":[
            {
          "title": "偶然發現的一天",
          "content": "講述了扮成女人潛伏在神祕寡婦村的男孩和不想成為妓生的女孩各自懷著祕密相遇後的故事。全綠豆，是一個外貌、體力和智商都相當出色的男人，還夢想成為最棒的「將軍」。受到意外事件影響，他必須過著躲躲藏藏的生活，為了找尋自己出生的祕密，以「男扮女裝」的身分躲進寡婦村，並與東東珠結緣。",
          "episode": "32集",
          "region": "韓國",
          "year": "2019",
          "type": ["愛情","喜劇"],
          "actor" : ["張東尹","金所泫"] ,      
          "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
          "video": "https://github.com/uiuxcafe/firstbank-landingpage/blob/master/video/eros.mp4"
       }
        ]
    }
}
```

- Server Response [無預告 link]

```json
{ 
    "data": {
        "drama":[
            {
          "title": "偶然發現的一天",
          "content": "講述了扮成女人潛伏在神祕寡婦村的男孩和不想成為妓生的女孩各自懷著祕密相遇後的故事。全綠豆，是一個外貌、體力和智商都相當出色的男人，還夢想成為最棒的「將軍」。受到意外事件影響，他必須過著躲躲藏藏的生活，為了找尋自己出生的祕密，以「男扮女裝」的身分躲進寡婦村，並與東東珠結緣。",
          "episode": "32集",
          "region": "韓國",
          "year": "2019",
          "type": ["愛情","喜劇"],
          "actor" : ["張東尹","金所泫"] ,      
          "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
          "video": null
       }
        ]
    }
}
```

## 2.2 分集大綱詳細頁
_進入分集大綱列表後，點選任一分集大綱，即打此 api，取得該集大綱詳細頁資訊。_ 

- Query
 
```
    query {
       drama (id: "1") 
       {
           outline (id: "1")
            {
                title
                episode 
                content
                img
            }
        }
```


- Server Response

```json
{ 
    "data": {
        "outline":[
        {
          "title": "端午發現記憶片斷化自我意識開始覺醒",
          "episode": "1",
          "content": "殷端午，一個富裕家庭的獨生女，Three貴族高中的風雲人物，父親是當地有名的企業會長，雖然身患先天心臟病，卻在經歷了幾次手術後奇跡般地活了下來，而且還在兩家父親的撮合下，與同學白經早早地訂了婚。不過，雖然端午暗戀白經已長達十年之久，可白經對她這個病秧子卻絲毫沒有感覺。",
          "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png"
       }
        ]
    }
}
```
---












