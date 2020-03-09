<!-- TOC -->

- [1.新聞區](#1-新聞區)
  - [1.1 新聞輪播列表]
  - [1.2 新聞列表頁]
  - [1.3 新聞詳細頁]
  

<!-- /TOC -->
# 1.新聞區
## 1.1 新聞輪播列表

_進入新聞、戲劇首頁時，打此 api，即顯示輪播列表。不限內容數量，採用人工調整。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]

### 新聞
- Query
 
```
query MyQuery {
  news_carousel {
    id
    caption
    cover
  }
}


- Response

```json
{
  "data": {
    "news_carousel": [
      {
        "id": 1,
        "caption": "閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨？",
        "cover": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/f2695eec3bbf3d8277d9ecc724169093.jpg"
      },
      {
        "id": 4,
        "caption": "陳情少年團成團！團名TUBS，全名是The Untamed Boys – TUBS",
        "cover": "https://p1.pstatp.com/large/pgc-image/1f91025e9f4d434e9284a93ee3a4e61e?/1.jpg"
      },
      {
        "id": 7,
        "caption": "《愛的迫降》李政赫尹世麗再遇阻攔，幕後大boss身份終於曝光",
        "cover": "http://p1.pstatp.com/large/pgc-image/f8611e06ba584c63b47b5e95b59ac82b?/1.jpg"
      }
    ]
  }
}
```

---

## 1.2 新聞列表頁
_進入新聞、戲劇、討論首頁時，打此 api，即顯示最新列表。_

_前端規則：當資料不足 10 筆（戲劇為 15筆），視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10（戲劇 offset：15）。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]


### 新聞
- Query
 
```
query MyQuery {
  news(limit: 3, order_by: {created_at: desc}) {
    id
    title
    thumbnail
    created_at
    excerpt
  }
}
```

- Response

```json
{
  "data": {
    "news": [
      {
        "id": 12,
        "title": "解析《陳情令》魏無羨人物主題曲「曲盡陳情」歌詞中的含義",
        "thumbnail": "http://p3.pstatp.com/large/pgc-image/3dfd9f046c4649f1bbe6ce2f7122ed7c?/1.jpg",
        "created_at": "2020-03-02T17:00:34.345501",
        "excerpt": "陳情令沒有更新的日子里我們等的度日如年，每天都期待著下周能早點到來，沒關係，今天已經周末了，只要等周一就可以來到十六年前的高甜部分啦！想想就很期待呢！在沒有更新的日子里，我們的主角們也都發了自己人物的主題曲，好聽自然是不必說了，但里邊的暗藏的小心思，你發現了嗎?"
      },
      {
        "id": 11,
        "title": "《親愛的熱愛的》番外篇佟年生了龍鳳胎韓商言變奶爸",
        "thumbnail": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/11a0653ffd489477d93c59f9792c696d.jpg",
        "created_at": "2020-03-02T16:59:06.302362",
        "excerpt": "說到韓國的犯罪懸疑韓劇，想必大家想到的是深入人心的《信號》，韓劇在犯罪懸疑題材方面近幾年的崛起速度很快，除了深入人心的《信號》之外，還有多部好看的犯罪韓劇。"
      },
      {
        "id": 10,
        "title": "9部韓國必看的懸疑推理劇，每部都在燒腦！",
        "thumbnail": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/07/d1a67a4809c374d31584ceacc16832be.jpg",
        "created_at": "2020-03-02T16:58:15.017665",
        "excerpt": "說到韓國的犯罪懸疑韓劇，想必大家想到的是深入人心的《信號》，韓劇在犯罪懸疑題材方面近幾年的崛起速度很快，除了深入人心的《信號》之外，還有多部好看的犯罪韓劇。"
      },
    ]
  }
}
```

## 1.3 新聞詳細頁
_點選新聞、戲劇首頁任一新聞、戲劇後，打此 api，即取得該篇新聞、戲劇詳細資料。_ 

- 新聞 WF [https://whimsical.com/6peTte9KXein4Za26dMfTQ]

### 新聞

- Query 
  
```
query MyQuery {
  news(where: {id: {_eq: "1"}}) {
    title
    created_at
    content
    thumbnail
    news_types {
      type_id
      type {
        name
        label
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
        "thumbnail": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/f2695eec3bbf3d8277d9ecc724169093.jpg",
        "news_types": [
          {
            "type_id": 15,
            "type": {
              "name": "懸疑",
              "label": "taxonomy"
            }
          },
          {
            "type_id": 33,
            "type": {
              "name": "張韶涵",
              "label": "tag"
            }
          },
          {
            "type_id": 610,
            "type": {
              "name": "范瑋琪",
              "label": "tag"
            }
          },
          {
            "type_id": 611,
            "type": {
              "name": "綠豆傳",
              "label": "tag"
            }
          }
        ]
      }
    ]
  }
}
```
