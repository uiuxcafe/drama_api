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
      - [新聞](#新聞-2)
      - [戲劇](#戲劇-2)
      - [討論](#討論-1)
    - [篩選搜尋](#篩選搜尋)
      - [類別](#類別)
      - [地區](#地區)
    - [相關結果搜尋](#相關結果搜尋)
      - [相關新聞](#相關新聞)
      - [相關戲劇](#相關戲劇)
      - [相關討論](#相關討論)
- [2. 詳細](#2-詳細)
  - [2.1 首頁詳細頁](#21-首頁詳細頁)
    - [新聞](#新聞-3)
    - [戲劇](#戲劇-3)
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
       carousel (where: {type: {_eq: "news"}})
       {
          id
          title
          cover
       }
    }

```
<!-- - mutation [新增] //不太確定如何打，如何加入帶入要新增的位置 news/drama?

```
    insert_carousel {
       {
          id: 6
          title: 閨蜜撕破臉！?,
          cover: https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png,
       }
    }
    
```

- mutation [更新] //不太確定如何打

```
    update_carousel {
       {
          id: 6
          title: 閨蜜撕破臉！?,
          cover: https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png,
       }
    }
    
```

- mutation [刪除] //不太確定如何打

```
    delete_carousel {
       {
          id: 6
          title: 閨蜜撕破臉！?,
          cover: https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png,
       }
    }
``` -->

### 戲劇
- Query
 
```
    query {
       carousel (where: {type: {_eq: "drama"}})
       {
          id
          title
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "":[
            {
            "id": 1,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```

---

## 1.2 首頁列表
_進入新聞、戲劇、討論首頁時，打此 api，即顯示最新列表。_

_前端規則：當資料不足 10 筆（戲劇為 15筆），視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10（戲劇 offset：15）。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]
- 戲劇 WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]
- 討論 WF [https://whimsical.com/JFAQ65FCGBdjmua5EDxENp]


### 新聞
- Query
 
```
    query {
       news (limit: 10, order_by: {post_date: desc}, offset: 10)
       {
          id
          title
          date
          excerpt
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "news":[
            {
            "id": 1,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-23 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-20 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-19 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-12 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
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
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"抓住幽靈",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"那一天",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"忠孝節義路遙知馬力",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 15,
            "title":"還是不能結婚的男人",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
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
          cover
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
          cover
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
          cover
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
          cover
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
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "forum":[
            {
            "id": 1,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-23 2:37:56",
            "source": "ptt",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-20 2:37:56",
            "source": "dcard",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-19 2:37:56",
            "source": "ptt",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"[情報] 紙房子第四季",
            "date": "2019-05-12 2:37:56",
            "source": "dcard",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```

## 1.3 分集大綱列表
_進入戲劇詳細頁後，點選下方分頁「分集大綱」，即打此 api 顯示該劇分集大綱。_

_前端規則：當資料不足 10 筆，視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10。_

<font color=#FFAA33>
Q:
1.按照集數排序應該如何寫？ 
</font>

- 分集大綱 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

- Query 
```
    query {
       drama (id: "1", season:"1") 
       { 
           episode (limit: 10, order_by: {episode: desc}) 
            {
                id
                title
                episode // 集數
                content // 預覽資訊 限制只顯示前20字 
                cover
            }
       }
    }

```


- Response

```json
{ 
    "data": {
        "outline":[
            {
            "id": 1,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"1",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"2",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"3",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 4,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"4",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 5,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"5",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 6,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"6",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 7,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"7",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 8,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"8",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 9,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"9",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 10,
            "title": "端午發現記憶片斷化自我意識開始覺醒",
            "epoisode":"10",
            "content":"殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",  
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
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
       trend  
       {
          name
       }
    }
    
```

- Response

```json
{ 
    "data": {
        "trend":[
            {
            "name":"延禧攻略",
        },
        {
            "name":"2019",
        },
        {
            "name":"金所炫",
        },
        ...
        {
            "name":"延禧",
        },
        ]
    }
}
```

<!-- - mutation [新增] //不太確定如何打

```
    insert_trend {
       {
          id: 11,
          name: 2018
       }
    }
    
```

- mutation [更新] //不太確定如何打

```
    update_trend {
       {
          id: 11,
          name: 2018
       }
    }
    
```

- mutation [刪除] //不太確定如何打

```
    delete_trend {
       {
          id: 11,
          name: 2018
       }
    }
    
``` -->

## 1.5 搜尋結果列表
_當用戶透過輸入關鍵字、點選 Tag 搜尋戲劇相關資料，輸入完畢點選送出，即可打此 API。_

_前端規則：當資料不足 10 筆，視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10。_


- 關鍵字/ Tag 搜尋 WF [https://whimsical.com/6yDEHPB1YTN3Q8T9FU6Gop]
- 篩選結果 WF [https://whimsical.com/4WBuD65bkGkLVhESwb4pY1]
- 相關結果 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]


### 關鍵字搜尋 | Tag 搜尋
_用戶直接在 search bar 關鍵字，點選送出，即可依據關鍵字顯示結果列表。_

_用戶點選新聞詳細頁的 Tag 後，即可打此 api，即可依據 Tag顯示結果列表。_

#### 新聞

- query 
```
    query {
       news (where: {title: {_ilike: "%延禧%"}},limit: 10, order_by: {post_date: desc}, offest:10)
       {
          id
          title
          date
          excerpt
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "news":[
            {
            "id": 1,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-23 2:37:56",
            "excerpt": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-22 2:37:56",
            "excerpt": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-21 2:37:56",
            "excerpt": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"《延禧攻略》劇好看！但金惠允被稱史上顏值",
            "date": "2019-05-15 2:37:56",
            "excerpt": "殷端午，一個富裕家庭的獨生女，Three 貴族高中的風雲人物",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```
#### 戲劇

- query 
```
    query {
       drama (where: {title: {_ilike: "%延禧%"}},limit: 10, order_by: {post_date: desc}, offest:10)  
       {
          id
          title
          year
          actor
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"延禧攻略",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "郭俊辰"
                }
              },
              {
              "actor": {
                "name": "李沁"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"延禧",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "郭俊辰"
                }
              },
              {
              "actor": {
                "name": "李沁"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"延禧攻",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "郭俊辰"
                }
              },
              {
              "actor": {
                "name": "李沁"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"延禧攻略x略",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "郭俊辰"
                }
              },
              {
              "actor": {
                "name": "李沁"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```
#### 討論

- query
```
    query {
       forum (where: {title: {_ilike: "%延禧%"}},limit: 10, order_by: {post_date: desc}, offest:10)  
       {
          id
          title
          date
          source
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "forum":[
            {
            "id": 1,
            "title":"[情報] XXX 有望演出《延禧攻略》",
            "date": "2019-05-23 2:37:56",
            "source": "PTT",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"#討論 延禧攻略 皇上 v.s. 傅恆",
            "date": "2019-05-23 2:37:56",
            "source": "PTT",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"[心得] 出不了坑的延禧攻略 (有雷)",
            "date": "2019-05-23 2:37:56",
            "source": "Dcard",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 10,
            "title":"[心得] 出不了坑的延禧攻略 (有雷)",
            "date": "2019-05-23 2:37:56",
            "source": "PTT",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```

### 篩選搜尋
_用戶在戲劇區時，可選擇以類型、地區進行篩選相關戲劇，篩選完畢即可打此 api，更新戲劇列表資料。_

_前端規則：當資料不足 15 筆時，視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 15。_

#### 類別

- query

```
    query {
       drama (where: {type: {_ilike: "%愛情%","%劇情%"}},limit: 15, order_by: {post_date: desc}, offest:15)  
       {
          id
          title
          cover
       }
    }

```

- Response 

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 15,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```
#### 地區

- query
```
    query {
       drama (where: {region: {_ilike: "%歐美%"}},limit: 15, order_by: {post_date: desc}, offest:15)  
       {
          id
          title
          cover
       }
    }

```

- Response 

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ...
        {
            "id": 15,
            "title":"喜歡的話請響鈴",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```

### 相關結果搜尋
_當用戶進入新聞、戲劇詳細頁時，打此 api 下方會顯示相關新聞、戲劇、討論結果列表。_

<!-- 自產新聞，由 nara 想好規則後，再補上。 -->

#### 相關新聞

- query
```
    query {
       news (where: {title: {_ilike: "%綠豆傳%"}},limit: 3, order_by: {post_date: desc})  
       {
          id
          title
          date
          excerpt
          cover
       }
    }

```
- Response
  
```json
{ 
    "data": {
        "news":[
            {
            "id": 1,
            "title":"綠豆傳撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-23 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"閨蜜撕破臉！綠豆傳到底發生過什麼恩怨?",
            "date": "2019-05-20 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨綠豆傳?",
            "date": "2019-05-19 2:37:56",
            "excerpt": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        ]
    }
}
```

#### 相關戲劇

- query
```
    query {
       drama (where: {title: {_ilike: "%綠豆傳%"}},limit: 3, order_by: {post_date: desc})  
       {
          id
          title
          year
          actor
          cover
       }
    }

```

- Response

```json
{ 
    "data": {
        "drama":[
            {
            "id": 1,
            "title": "抓住幽靈",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "姜河那"
                }
              },
              {
              "actor": {
                "name": "孔曉振"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"那一天",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "姜河那"
                }
              },
              {
              "actor": {
                "name": "孔曉振"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"忠孝節義路遙知馬力",
            "year": "2019",
            "drama_actors": [
              {
              "actor": {
                "name": "姜河那"
                }
              },
              {
              "actor": {
                "name": "孔曉振"
              }
              }
            ],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        }
        ]
    }
}
```
#### 相關討論

- query
```
    query {
       forum (where: {title: {_ilike: "%九%"}},limit: 3, order_by: {post_date: desc}) 
       {
          id
          title
          date
          source
          cover
       }
    }
    
```

- Response

```json
{ 
    "data": {
        "forum":[
            {
            "id": 1,
            "title":"[情報] XXX 有望演出《延禧攻略》",
            "date": "2019-05-23 2:37:56",
            "source": "PTT",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"#討論 延禧攻略 皇上 v.s. 傅恆",
            "date": "2019-05-23 2:37:56",
            "source": "PTT",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"[心得] 出不了坑的延禧攻略 (有雷)",
            "date": "2019-05-23 2:37:56",
            "source": "Dcard",
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
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
      news(where: {id: {_eq: "1"}}) {
        title
        created_at
        content
        cover
        news_types {
          type {
            name
            type
          }
        }
      }
    }
```

- Response 

```json
{
  "data": {
    "news": [
      {
        "title": "閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨？",
        "created_at": "2019-12-19T17:23:10.666013",
        "content": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
        "cover": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/f2695eec3bbf3d8277d9ecc724169093.jpg",
        "news_types": [
          {
            "type": {
              "name": "懸疑",
              "type": "type"
            }
          },
          {
            "type": {
              "name": "張韶涵",
              "type": "tag"
            }
          }
        ]
      }
    ]
  }
}
```

### 戲劇
_有預告link 先顯示預告，沒有 預告link 則顯示封面cover。_

- Query
 
```
    query {
        drama(where: {id: {_eq: "1"}}) {
          title
          season
          excerpt
          episode
          status
          year
          drama_actors {
            actor {
              name
            }
          }
          drama_types {
            type {
              name
              type
            }
          }
          cover
          teaser
        }
       }
```

- Response [有預告 link]

```json
{
  "data": {
    "drama": [
      {
        "title": "山茶花開時",
        "season": 1,
        "excerpt": "《山茶花開時》講述的是一個孤兒冬柏長大后成為單身母親的故事。她開了一家居酒屋，名為“冬柏”，中文意思是山茶花。龍植是鎮上一名正義滿滿的巡警，在遇到他之後，冬柏的生活發生了轉折。他們不顧世俗對單親媽媽的偏見而墜入愛河。龍植從小由媽媽獨自撫養長大，明白冬柏這一路走來有多麼艱辛，所以想要用一生去守護她。",
        "episode": 18,
        "status": "連載中",
        "year": 2019,
        "drama_actors": [
          {
            "actor": {
              "name": "郭俊辰"
            }
          },
          {
            "actor": {
              "name": "李沁"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "韓劇",
              "type": "category"
            }
          },
          {
            "type": {
              "name": "韓國",
              "type": "region"
            }
          },
          {
            "type": {
              "name": "年度必看",
              "type": "tag"
            }
          },
          {
            "type": {
              "name": "現代",
              "type": "type"
            }
          },
          {
            "type": {
              "name": "愛情",
              "type": "type"
            }
          }
        ],
        "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        "teaser": "https://www.youtube.com/watch?v=jMMFJDn_WaM"
      }
    ]
  }
}
```

- Response [無預告 link]

```json
{
  "data": {
    "drama": [
      {
        "title": "山茶花開時",
        "season": 1,
        "excerpt": "《山茶花開時》講述的是一個孤兒冬柏長大后成為單身母親的故事。她開了一家居酒屋，名為“冬柏”，中文意思是山茶花。龍植是鎮上一名正義滿滿的巡警，在遇到他之後，冬柏的生活發生了轉折。他們不顧世俗對單親媽媽的偏見而墜入愛河。龍植從小由媽媽獨自撫養長大，明白冬柏這一路走來有多麼艱辛，所以想要用一生去守護她。",
        "episode": 18,
        "status": "連載中",
        "year": 2019,
        "drama_actors": [
          {
            "actor": {
              "name": "郭俊辰"
            }
          },
          {
            "actor": {
              "name": "李沁"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "韓劇",
              "type": "category"
            }
          },
          {
            "type": {
              "name": "韓國",
              "type": "region"
            }
          },
          {
            "type": {
              "name": "年度必看",
              "type": "tag"
            }
          },
          {
            "type": {
              "name": "現代",
              "type": "type"
            }
          },
          {
            "type": {
              "name": "愛情",
              "type": "type"
            }
          }
        ],
        "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        "teaser": null
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
      episode(where: {drama: {title: {_eq: "慶餘年"}, season: {_eq: 1}}}) {
        title
        season
        episode
        content
        cover
      }
    }
```


- Response

```json
{
  "data": {
    "episode": [
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 1,
        "content": "現代青年一朝穿越 范閒拜師醫毒雙絕\t一個患有重症肌無力的現代青年，一覺醒來，發現自己穿越成了一個古代嬰兒，正躺在一個竹籃里，遭受一群殺手的圍攻追殺，疑惑之間，一個屬於他的嶄新世界，迎面而來。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 2,
        "content": "縢梓荊接到假命令刺殺范閒 范少爺欲尋真相執意上京都\t到了吃飯的時候，那群紅甲騎士依舊跪在院中，老夫人卻沒事人一般，招呼范閒吃飯。范閒發現桌上有一盤新鮮的竹筍，連忙搶到自己跟前，三兩口扒進了嘴裡，邊吃便問起今天往府里送菜的是不是老哈。周管家答說，老哈病了，今天是他侄子來送的菜，范閒又問了他侄子是否來過府中，得到否定的回答後，他匆匆一抹嘴，稱自己吃飽了，然後向老夫人施了禮，起身離開了。周管家見此情形，想要告范閒的黑狀，老夫人卻深深地看了他一眼，周管家知道自己逾矩了，連忙住嘴。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 3,
        "content": "慶帝設計敲打臣子 范閒回府智斗姨娘\t范閒以為這個神廟之行，是背後想要殺自己的那人布下的一個局，他懷著一腔好奇進入了神廟，但小心翼翼地在廟裡轉了一圈後，他發現並沒有埋伏，他暗想，原來是自己猜錯了。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 4,
        "content": "太子暗地奪權遭申飭 范閒不滿婚約欲退親\t范閒進了書房後，范建讓他將門關上，自己卻坐下來又是翻書又是寫字，根本不理范閒。范閒也不急，就站在案前安靜地等待著，范建忙完了之後，開門見山地問范閒，他想做個什麼樣的人。范閒也不客氣，稱自己想要富甲天下，嬌妻美妾，一生平安。范建聽了，面無表情地又問他憑什麼起家，范閒稱自己有一項獨門絕技，可以在高溫之下，用砂礫做出光滑透明的玻璃，范建聞言，向他舉了舉案上的玻璃茶杯，范閒不禁愕然，得知這東西是自己的母親葉輕眉當年做出來的，而且不止於此，就連肥皂、香皂、白砂糖這些他想要拿來橫行古代世界的東西，母親都曾做出來過，他不禁嘆息：既生兒，何生娘。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 5,
        "content": "范閒得知縢梓荊過往惺惺相惜 各方勢力紛紛矚目范家私生子\t縢梓荊之所以來找范閒，是因為在澹州的時候，見他有提司的腰牌，這才來求他，到鑒查院為自己取一份無關緊要的文書，並稱事成之後，自己這條命便交給他，由他掌控。范閒卻表示不願意，他要的不是縢梓荊的命，他只想知道，縢梓荊身上發生的故事。縢梓荊見狀，便一五一十的將自己遭通緝的緣由告訴了他。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 6,
        "content": "太子命人敗壞范公子名聲 范閒私調縢梓荊當年文卷\t葉靈兒認出是范府的馬車，也看到了范若若，便告訴了自己身邊的林婉兒，林婉兒執意要見上范閒一面，范若若為了不讓人發現范閒不在車上，千方百計阻攔，林婉兒卻一再堅持。正當范若若無計可實時，范思轍在車上抓耳撓腮地想出了一個辦法，他故意沉下聲音，冒充范閒出言道，自己剛剛去喝酒，叫了一個唱曲的小娘子，如今正在自己車上，不方便與她交談。林婉兒聞言，連連咳嗽，又吐出一口血來，葉靈兒見狀，狠狠瞪了范家的馬車一眼，上車與林婉兒離開了。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 7,
        "content": "賽詩會范閒力拔頭籌 二皇子紆尊與之結交\t見兒子堅持，范建終於答應放了縢梓荊，范閒再次要求父親向范思轍道歉，范思轍卻拉不下這個臉，不悅地拂袖而去。柳如玉一直在一旁看著這一幕，見范閒是真心替兒子求情，心中也十分感動，上前向范閒致謝，並表示，從今後只要范閒不針對自己，自己決不給他找麻煩。范閒聞言，心中鬆了口氣，多個朋友總比多個敵人強，雖然柳如玉還算不上他的朋友，但至少不再站在自己的對立面上，這就是一大進步了。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 8,
        "content": "王啟年呈上假文案 縢梓荊輾轉見妻兒\t二皇子想跟范閒談談與太子的事，范閒卻不接話，反而自顧自地跟他說起了自己與雞腿姑娘的邂逅，並篤定地表示，自己與她一見鍾情，定要娶她。二皇子聞言，不禁啞然失笑，范閒的婚姻，關乎到內庫財權，且為慶帝親自指婚，怎么可能由著他說了算？但見范閒一副胸有成竹的樣子，也不便打擊他，便稱自己拭目以待，等著看他怎樣大鬧京都。說完，二皇子拿起石桌上的那本《紅樓》，揚長而去。范閒見二皇子拿著的，竟然是自己寫的書，不禁瞪大了眼睛。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 9,
        "content": "官差上門捉拿范閒被柳如玉攔阻 范閒公堂受審各路大神紛紛現身\t王啟年此人滑不留手，發現也知道，從他口中聽不到實話，也就不再追問那些不可能發生的事了，只是鄭重謝過了他對縢梓荊妻兒的維護之情。王啟年一聽，立刻拿出了一張地契，稱自己買下這個小院落，花了一百二十三兩銀子，讓范閒給自己湊個整，，拿一百三十兩銀子出來。范閒稱自己身上沒那么多錢，讓他到府上去拿，王啟年一聽，又奪回了那張地契，生怕范閒不認賬似的范閒不禁哭笑不得。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 10,
        "content": "公堂對質不了了之 范閒登門尋人未果\t范閒當面問太子，之前自己在澹州被刺殺，可與他有關。二皇子聞言，暗中向范閒伸出了大拇指，太子則冷哼一聲，逕自離開了。侯公公又告訴梅執禮，慶帝在宮中等著召見他，梅執禮連忙遵旨而去。范閒認出了侯公公便是那天趕車送自己去慶廟的人，問他自己怎么辦，侯公公笑著告訴他，審案的人都走了，自然是各回各家，各找各媽。這話一出，不僅是郭保坤，連范閒都有些摸不著頭腦，不知道慶帝這是玩兒的哪一出。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 11,
        "content": "范閒找到雞腿姑娘 婉兒得知范閒身份\t范閒找不到雞腿姑娘，不肯罷休，便想從根源上入手，讓林婉兒自己出面，退了這門親事，於是便帶著范若若他們，直接去了林婉兒養病的皇家別院。范閒以醫者的身份，隨著范若若進了別院，長公主留在這裡的侍女得知了他們的來意，連忙飛鴿傳書，將此事稟報了長公主。長公主猜出了范閒的來意，便同意了讓他們見面。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 12,
        "content": "葉靈兒訪司理理被人所傷 長公主得知女兒心悅范閒\t侍女走後，葉靈兒湊近裝睡的林婉兒，問她范閒哪裡去了，藏在林婉兒被子裡的范閒猛然露出頭來，嚇了葉靈兒一跳，她見狀又知趣地躲了出去。葉靈兒離開後，范閒還是沒有起身的打算，林婉兒覺得尷尬，便又是拉又是扯地催促他起來。范閒不想她著急，便聽話地起了身，但他不捨得離開，於是坐在床頭，給林婉兒講起了故事，兩人說說笑笑，好不開心。聊了半晌，林婉兒忽然想起了司理理，便說起兩人的曖昧傳言，范閒連忙賭咒發誓地向她解釋，兩人之間清清白白，自己做那一切都是為了悔婚，帶著雞腿姑娘浪跡天涯。林婉兒聽了，心中頗感甜蜜。 范閒此時慶幸不已，幸虧自己的婚約里遇到的是自己心愛的人，林婉兒也做如是想。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 13,
        "content": "縢梓荊被暴徒所殺 范閒不顧一切尋仇\t二皇子和李弘成早早就到了醉仙居，兩人一邊悠閒地吃著瓜果，一邊等著范閒。司理理動作優雅嫻熟地為二皇子泡了一杯茶，卻在呈給他的時候，茶杯突然裂開。二皇子見狀，不由心中一動，覺得此事不詳。此時，范閒正和縢梓荊趕著馬車，說說笑笑趕往醉仙居。當他們走到郭保坤當天晚上被打的那條街時，忽然出現兩個蒙面女子，向兩人頻頻射箭。縢梓荊是用暗器的祖宗，自然不會被這些雕蟲小技難住，三兩下就解決了其中一個。范閒在一時間的慌亂後，也也鎮定了下來，很快將另一個女殺手也解決掉了。然而讓他想不到的是，更大的危險還在後面，就在他再次躲開前面埋伏的巨弩後，被旁邊牆內的程巨樹隔著牆扼住脖子，扔進了院裡。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 14,
        "content": "慶帝赦免范閒殺人之罪 王啟年偷取密報被免職\t朱格派來押送程巨樹的兩個人，想要攔住范閒，放走程巨樹，卻被程巨樹一邊一掌拍了開去。他小山似的身軀走向范閒，想要與他搏殺一番，卻不想一個照面就被范閒手中的匕首刺中了要害。這把匕首是范閒初進京時，縢梓荊贈與他的，如今用來為他報仇，再合適不過了。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      },
      {
        "title": "慶餘年",
        "season": 1,
        "episode": 15,
        "content": "司理理高調出逃意欲混淆視聽 范閒縝密分析得知對手路線\t王啟年將自己調查的結果告訴了范閒，稱那塊腰牌是北齊暗線的腰牌，北齊密探就是靠這塊令牌調動屬下行事。范閒懷疑，程巨樹就是北齊的密探，不禁苦笑，不知自己又和德能，竟讓不知名的大人物聯合北齊密探，來取自己的小命。",
        "cover": "http://pix1.tvzhe.com/focuspic/drama/70327/cate_focus_pic.jpg"
      }
    ]
  }
}
```
---












