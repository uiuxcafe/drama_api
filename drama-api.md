<!-- TOC -->

- [1.新聞區](#1新聞區)
  - [1.1 新聞輪播列表](#11-新聞輪播列表)
  - [1.2 新聞列表](#12-新聞列表)
    - [最新列表](#最新列表)
    - [熱門列表 [等待後端資料齊全再開發]](#熱門列表-等待後端資料齊全再開發)
  - [1.3 新聞詳細頁](#13-新聞詳細頁)
- [2. 戲劇區](#2-戲劇區)
  - [2.1 戲劇輪播列表](#21-戲劇輪播列表)
  - [2.2 戲劇列表](#22-戲劇列表)
    - [最新列表](#最新列表-1)
    - [熱門列表[等待後端資料齊全再開發]](#熱門列表等待後端資料齊全再開發)
  - [2.3 戲劇詳細頁](#23-戲劇詳細頁)
  - [2.4 分集大綱列表](#24-分集大綱列表)
  - [2.5 分集大綱詳細頁](#25-分集大綱詳細頁)
- [3. 討論區](#3-討論區)
  - [3.1 討論列表](#31-討論列表)
    - [最新列表](#最新列表-2)
    - [熱門列表[等待後端資料齊全再開發]](#熱門列表等待後端資料齊全再開發-1)
- [4. 搜尋](#4-搜尋)
  - [4.1 搜尋結果列表](#41-搜尋結果列表)
    - [關鍵字搜尋](#關鍵字搜尋)
    - [Tag 搜尋](#tag-搜尋)
    - [篩選搜尋](#篩選搜尋)
  - [4.2 熱門關鍵字列表](#42-熱門關鍵字列表)
  - [4.3 相關結果列表](#43-相關結果列表)

<!-- /TOC -->

# 1.新聞區
主要文章來源來自「尋夢新聞」、「自產文章」。

## 1.1 新聞輪播列表
_進入新聞首頁時，打此 api，即顯示輪播列表。_ 

_不限內容數量，採用人工調整。_

- WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]

- Query 
 
```

    query {
       carosell (where: {type: {_eq: “news“}})
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


## 1.2 新聞列表
_進入新聞首頁時，打此 api，即顯示新聞列表。會依據 **最新、熱門** 條件顯示新聞列表。_

- WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]

- 條件

    <ol>
    <li> 預設採用 最新發佈時間 排序顯示列表。 </li>
    <li> 一次載入 10篇 內容。</li>
    <li> 熱門列表 等待後端資料足夠再行開發。</li>
    </ol>

### 最新列表

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
        {
            "id": 4,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-18 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 5,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-17 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 6,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-16 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 7,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-15 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 8,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-14 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 9,
            "title":"閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨?",
            "date": "2019-05-13 2:37:56",
            "preview": "近段時間張韶涵在歌手的舞台上再次收穫大量關注度，於是她和范瑋琪當年的“翻臉閨蜜恩怨史”又鬧到了檯面上。",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
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

### 熱門列表 [等待後端資料齊全再開發]
_在新聞首頁點選「排序」按鈕時，點選熱門排序，打此 API，即依據一週內新聞按 **尋夢新聞觀看次數由多至少** 排序。_

## 1.3 新聞詳細頁
_點選新聞首頁任一新聞後，打此 api，即取得該篇文章詳細資料。_ 
_採集資源來自：尋夢新聞_

- WF [https://whimsical.com/6peTte9KXein4Za26dMfTQ]

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
---

# 2. 戲劇區
主要戲劇收集的區間先從 2019/12月~2020/01月。

## 2.1 戲劇輪播列表
_進入戲劇首頁時，打此 api，即顯示戲劇輪播列表。_

_不限戲劇輪播數量，目前以手工為主？_

- WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]

- Query 
 
```

    query {
       carosell (where: {type: {_eq: “drama“}})
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
            "title":"長安十二時辰",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 2,
            "title":"綠豆傳",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 3,
            "title":"親愛的，熱愛的",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```
## 2.2 戲劇列表
_進入戲劇首頁時，打此 api，即顯示戲劇列表資料。會依據 **最新、熱門** 條件顯示新聞列表。_

- WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]

- 條件
  <ol>
    <li> 預設採用 **最新更新時間順序由上至下** 排列。</li>
    <li> 一次取得 15 齣戲劇資料。</li>
    <li> 熱門列表等待後端資料齊全後開發。</li>
  </ol>

### 最新列表
_進入戲劇首頁時，打此 api，列表即依據 **最新更新時間順序由上至下** 顯示。_

- Query
 
```
    query {
       drama (limit: 15, order_by: {post_date: desc}, offset: 15)  // limit:一次取10筆，order_by:最新順序由上至下，offset: 取第10筆之後
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
        {
            "id": 4,
            "title":"HIStory3-那一天",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 5,
            "title":"忠孝節義斷機教子",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 6,
            "title":"鶴唳華亭",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 7,
            "title":"十年三月三十日",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 8,
            "title":"Healer/治癒者",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 9,
            "title":"偶然發現的一天",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 10,
            "title":"山茶花開時",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 11,
            "title":"當你沉睡時",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 12,
            "title":"東京大飯店",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 13,
            "title":"求婚大作戰",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 14,
            "title":"不能結婚的男人",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        {
            "id": 15,
            "title":"還是不能結婚的男人",
            "img": "https://github.com/uiuxcafe/uiuxcafe_web/blob/master/src/img/service/icon_01.png",
        },
        ]
    }
}
```


### 熱門列表[等待後端資料齊全再開發]
_進入戲劇首頁時，打此 api，戲劇列表即以 **一個月內戲劇按評分（依據酷播爬評分）由高至低** 顯示。_


## 2.3 戲劇詳細頁
_點選戲劇首頁任一齣戲劇後，打此 api，即取得該部戲劇詳細資料。_ 

- WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

- 條件
  <ol>
  <li> 有預告link先顯示預告，沒有預告link則顯示封面</li>
  </ol>

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


## 2.4 分集大綱列表
_進入戲劇詳細頁，點選分集大綱，即打此 api，取得該戲劇分集大綱列表。_ 

- WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

## 2.5 分集大綱詳細頁
_點選分集大綱，即打此 api，取得該集大綱詳細。_ 

- WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

---

# 3. 討論區
主要戲劇收集的來源來自「PTT」、「Dcard」兩大平台。

## 3.1 討論列表
_進入討論首頁時，點選某一類別打此 api，即取得該類別的討論列表。_

- WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]

- 條件
    <ol>
    <li> 類別分為：美劇、陸劇、韓劇、日劇、台劇 共五類。</li>
    <li> 一頁顯示 10 篇文章。</li>
    <li> 預設採用 最新發佈時間 排序顯示列表。</li>
    <li> 熱門列表 等待後端資料齊全再開發。</li>
    </ol>

### 最新列表
_進入討論首頁時，打此 api，討論列表即依據 **最新發佈時間由上至下** 排序顯示列表。_

- 美劇

- 陸劇

- 韓劇

- 日劇

- 台劇

### 熱門列表[等待後端資料齊全再開發]
_進入討論首頁時，依據各地區列表點選「熱門」後，打此 api，討論列表即 **以一週內討論文章依留言數由多至少排序**。_

- 美劇

- 陸劇

- 韓劇

- 日劇

- 台劇

<!-- ## 3.2 討論詳細頁（等待我們有發文的機制，再行開發）
_點選討論首頁任一篇文章後，打此 api，即 modal 外連至該網站。_  -->

<!-- ## 3.3 討論輪播列表（等待後端資料齊全後開發）
_進入討論首頁時，依據各地區打此 api，取得該地區每天精選 5 篇熱門討論 **（以平台留言數為主）**。_ -->


---

# 4. 搜尋

## 4.1 搜尋結果列表
_當用戶透過輸入關鍵字、點選 Tag 搜尋戲劇相關資料，輸入完畢點選送出，即可打此 API。_

- 搜尋 WF [https://whimsical.com/6yDEHPB1YTN3Q8T9FU6Gop]
- 篩選 WF [https://whimsical.com/4WBuD65bkGkLVhESwb4pY1]

- 條件
  <ol>
    <li> 依據搜尋關鍵字，分別顯示三種類型的結果列表。</li> 
    <li> 搜尋類型分為三種：新聞、戲劇、討論。</li> 
    <li> 每一類型搜尋結果均回傳 3 筆資料。</li> 
    <li> 結果列表請以 最新發佈時間 排序，由上至下排序。</li> 
  </ol>

### 關鍵字搜尋
_用戶直接在 search bar 關鍵字，點選送出，即可依據關鍵字顯示結果列表。_

- 新聞（title）
- 戲劇 (title)
- 討論 (title)


### Tag 搜尋
_用戶點選新聞詳細頁的 Tag 後，即可打此 api，即可依據 Tag顯示結果列表。_

- 新聞
- 戲劇
- 討論

### 篩選搜尋
_用戶在戲劇區時，可選擇以類型、地區、年份進行篩選相關戲劇，篩選完畢即可打此 api，更新戲劇列表資料。_

- 類別
- 地區
- 年份

## 4.2 熱門關鍵字列表
_用戶點選搜尋後，打此 api 即顯示近期熱門搜尋關鍵字，用戶可點選任一關鍵字進行搜尋。_

- 條件
  <ol>
    <li>目前採用人工方式，每週（每天）更新。</li>
    <li>一次顯示 10 個關鍵字。</li>
  </ol>

## 4.3 相關結果列表
當用戶進入新聞、戲劇詳細頁時，打此 api 下方會顯示相關新聞、戲劇、討論結果列表。

- WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

- 條件
  <ol>
    <li>每一類型搜尋結果均回傳 3 筆資料。</li>
    <li>結果列表請以 最新發佈時間 排序，由上至下排序。</li>
  </ol>

- 相關新聞(title)

```
    query {
       news (where: {post_title: {_ilike: "%九%"},limit: 3, order_by: {post_date: desc})  
       {
          id
          title
          date
          preview
          img
       }
    }

```
- 相關戲劇(title)
- 相關討論(title)








