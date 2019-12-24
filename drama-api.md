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
            "actor": ["金所炫","張東尹"],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"那一天",
            "year": "2019",
            "actor": ["金所炫","張東尹"],
            "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"忠孝節義路遙知馬力",
            "year": "2019",
            "actor": ["金所炫","張東尹"],
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

<font color=#FFAA33>
待討論
</font>

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
                cover
            }
        }
```


- Response

```json
{ 
    "data": {
        "outline":[
        {
          "title": "端午發現記憶片斷化自我意識開始覺醒",
          "episode": "1",
          "content": "殷端午，一個富裕家庭的獨生女，Three貴族高中的風雲人物，父親是當地有名的企業會長，雖然身患先天心臟病，卻在經歷了幾次手術後奇跡般地活了下來，而且還在兩家父親的撮合下，與同學白經早早地訂了婚。不過，雖然端午暗戀白經已長達十年之久，可白經對她這個病秧子卻絲毫沒有感覺。",
          "cover": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/cover/service/icon_01.png"
       }
        ]
    }
}
```
---












