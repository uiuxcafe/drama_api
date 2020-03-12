<!-- TOC -->

- [1. 新聞區](#1-新聞區)
    - [1.1 新聞輪播列表](#11-新聞輪播列表)
    - [1.2 新聞列表頁](#12-新聞列表頁)
    - [1.3 新聞詳細頁](#13-新聞詳細頁)
    - [1.4 取得新聞tag列表](#14-取得新聞tag列表)
    - [1.5 新聞相關列表](#15-新聞相關列表)
- [2. 戲劇區](#2-戲劇區)
    - [2.1 戲劇輪播列表](#21-戲劇輪播列表)
    - [2.2 戲劇列表頁](#22-戲劇列表頁)
    - [2.3 戲劇詳細頁](#23-戲劇詳細頁)
    - [2.4 分集大綱列表](#24-分集大綱列表)
    - [2.5 分集大綱詳細](#25-分集大綱詳細)
    - [2.6 取得演員列表](#27-戲劇相關文章列表)
    - [2.7 戲劇相關文章列表](#27-戲劇相關文章列表)
    - [2.8 戲劇相關戲劇列表](#28-戲劇相關戲劇列表)
    - [2.9 戲劇相關討論列表](#29-戲劇相關討論列表)
- [3. 討論區](#3-討論區)
    - [3.1 討論列表頁](#31-討論列表頁)
- [4. 關鍵字](#4-關鍵字)
    - [4.1 熱門關鍵字列表](#41-熱門關鍵字列表)
- [5. 搜尋結果列表](#5-搜尋結果列表)
    - [5.1 關鍵字/Tag搜尋](#51-關鍵字/Tag搜尋)
    - [5.2 篩選搜尋](#52-篩選搜尋)
<!-- /TOC -->

# 1. 新聞區
## 1.1 新聞輪播列表

_進入新聞首頁時，打此 api，即顯示新聞輪播列表。不限內容數量，採用人工調整。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]

- Query

```
query {
  news_carousel {
    id
    caption
    cover
  }
}

```

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

_進入新聞首頁時，打此 api，即顯示新聞最新列表。_

_前端規則：當資料不足 10 筆（戲劇為 15 筆），視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10（戲劇 offset：15）。_

- 新聞 WF [https://whimsical.com/Syq3vMNvHrJpVEhjVJP3hY]

- Query

```
query {
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

_點選新聞後，打此 api，即取得該篇新聞詳細資料。_

- 新聞 WF [https://whimsical.com/6peTte9KXein4Za26dMfTQ]

- Query

```
query {
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
## 1.4 取得新聞tag列表

_用新聞id取得此新聞tag list_

- query
```
query {
  news_type(where: {news_id:{_eq: "1"}, type: {label: {_eq: "tag"}}}) {
    type {
      name
    }
  }
}

```
- Response
  
```json
{
  "data": {
    "news_type": [
      {
        "type": {
          "name": "張韶涵"
        }
      },
      {
        "type": {
          "name": "范瑋琪"
        }
      },
      {
        "type": {
          "name": "綠豆傳"
        }
      }
    ]
  }
}
```


## 1.5 新聞相關列表

_打api1.4取得tag list後接著再用回傳的關鍵字做 or query_

- query
```
query {
  news(where: {
    _or: [
      {title: {_ilike: "%美劇%"}}, 
      {title: {_ilike: "%閨蜜%"}}, 
      {title: {_ilike: "%陳情令%"}}
    ]}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    excerpt
    thumbnail
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
        "excerpt": "陳情令沒有更新的日子里我們等的度日如年，每天都期待著下周能早點到來，沒關係，今天已經周末了，只要等周一就可以來到十六年前的高甜部分啦！想想就很期待呢！在沒有更新的日子里，我們的主角們也都發了自己人物的主題曲，好聽自然是不必說了，但里邊的暗藏的小心思，你發現了嗎?",
        "thumbnail": "http://p3.pstatp.com/large/pgc-image/3dfd9f046c4649f1bbe6ce2f7122ed7c?/1.jpg"
      },
      {
        "id": 8,
        "title": "《陳情令》中藍湛胸口的烙印到底是怎麼弄成的？",
        "excerpt": "當年在玄武洞的時候。溫晁看上了綿綿。溫晁的女人王靈嬌看不過眼。就在大家都在對付屠戮玄武的時候拿起了烙鐵去想讓綿綿毀容。當時魏無羨看見了這一幕。看著離綿綿越來越近的烙鐵。魏無羨沖了上去。所以那個烙印就印在了他的胸口上。",
        "thumbnail": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/48ec8b1e529c4d818f2b9393a3029e0d.jpg"
      },
      {
        "id": 1,
        "title": "閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨？",
        "excerpt": "閨蜜撕破臉！張韶涵和范瑋琪到底發生過什麼恩怨？",
        "thumbnail": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/f2695eec3bbf3d8277d9ecc724169093.jpg"
      }
    ]
  }
}
```


# 2. 戲劇區

## 2.1 戲劇輪播列表

_進入戲劇首頁時，打此 api，即顯示戲劇輪播列表。不限內容數量，採用人工調整。_

- 戲劇 WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]

- Query

```
query {
  drama_carousel {
    id
    caption
    cover
  }
}


```

- Response

```json
{
  "data": {
    "drama_carousel": [
      {
        "id": 1,
        "caption": "我的情敵是自己",
        "cover": "https://hd.itsfun.com.tw/img/3/cad/wZwpmLHRDNxQjM1ckMyADMy0SMvcjMyADMy8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      },
      {
        "id": 7,
        "caption": "梨泰院Class",
        "cover": "https://hd.itsfun.com.tw/img/a/152/cGcq5SNxIDNGNTNxUjMyADMy0SMvUjMyADMy8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      },
      {
        "id": 10,
        "caption": "火影忍者",
        "cover": "https://hd.itsfun.com.tw/img/3/844/wZwpmL2hGM1Izai5mMzM3X4ETMwAjMwIzL4ETMw8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      },
      {
        "id": 6,
        "caption": "你好德古拉",
        "cover": "https://hd.itsfun.com.tw/img/e/a50/nBnauMDN1EzMxAjNxUjMyADMy0SMvUjMyADMy8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      }
    ]
  }
}
```

---

## 2.2 戲劇列表頁

_進入戲劇首頁時，打此 api，即顯示戲劇最新列表。_

_前端規則：當資料不足 10 筆（戲劇為 15 筆），視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10（戲劇 offset：15）。_

- 戲劇 WF [https://whimsical.com/S597ibFZnpwWm87yw8j6Dv]

- Query

```
query {
  drama(limit: 3, order_by: {created_at: desc}) {
    id
    title
    thumbnail
  }
}


```

- Response

```json
{
  "data": {
    "drama": [
      {
        "id": 27611,
        "title": "精神病醫師赫夫",
        "thumbnail": "https://img.58b.tv/movieimg/2014-06/53acf6c9f061c.jpg"
      },
      {
        "id": 27613,
        "title": "生活向前衝 第1季/生活向前沖",
        "thumbnail": "https://img.58b.tv/movieimg/2016-06/57608d97ab1ac.jpg"
      },
      {
        "id": 27606,
        "title": "添丁發財(新加坡)",
        "thumbnail": "https://img.58b.tv/movieimg/2010-11/4cd4491698677.jpg"
      },
    ]
  }
}
```

---

## 2.3 戲劇詳細頁

_點選戲劇後，打此 api，即取得該戲劇詳細資料。_

- 戲劇 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

_有預告 link 先顯示預告，沒有 預告 link 則顯示封面 thumbnail。_

- Query

```
query {
  drama(where: {id: {_eq: "43"}}) {
    title
    season
    episode
    excerpt
    status
    year
    teaser
    thumbnail
    created_at
    drama_actors(order_by: {actor: {count: desc}}) {
      actor {
        name
      }
    }
    drama_types {
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
    "drama": [
      {
        "title": "熱血同行",
        "season": 1,
        "episode": 58,
        "excerpt": " \t　　熱血同行劇情改編自漫畫《艷勢番》，主要講述了清末民初時期，皇親貴族組成的秘密組織“艷勢番”在動盪時局中早已腐朽傾頹，以崇利明為首的一眾擁有新思想的貴族青年，和平民少年阿易共同復興“艷勢番”，護衛家國的故事。\t　　清末亂世，留洋歸來的滿清貝勒崇利明破格招募因陰差陽錯而相識的阿易，加入了特殊宮廷護衛組織：艷勢番。歷經一系列殘酷選拔和任務考驗，阿易與艷勢番眾人結下深厚情誼，共同面對動盪時代的種種艱難險阻。而崇利明也隨著與洋人、黑幫以及腐朽滿清內部勢力的鬥爭，逐漸明白了友情、理想的真諦。\t　　隨著歷史浪潮不可逆轉的發展，阿易與崇利明一度理念相悖、漸行漸遠。最終，覺醒的阿易尋找到了投身革命救亡圖存的理想，加入革命黨與清廷勢力徹底決裂，崇利明也接受革命感召與阿易共同聯手，促成和平談判，成為歷史和平過渡的護航者，見證了清王朝的覆滅與新時代的來臨 。 ",
        "status": "完結",
        "year": 2020,
        "teaser": null,
        "thumbnail": "https://hd.itsfun.com.tw/img/f/6d8/wZwpmL2UzVBRTOGFTMxkTMtYTMvcTMxETOx8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg",
        "created_at": "2020-02-27T22:35:54.502973",
        "drama_actors": [
          {
            "actor": {
              "name": "黃子韜"
            }
          },
          {
            "actor": {
              "name": "易烊千璽"
            }
          },
          {
            "actor": {
              "name": "胡冰卿"
            }
          },
          {
            "actor": {
              "name": "馬澤涵"
            }
          },
          {
            "actor": {
              "name": "吳俊余"
            }
          },
          {
            "actor": {
              "name": "王瑞昌"
            }
          },
          {
            "actor": {
              "name": "劉芸"
            }
          },
          {
            "actor": {
              "name": "寧心"
            }
          },
          {
            "actor": {
              "name": "郭曉婷"
            }
          },
          {
            "actor": {
              "name": "苑子文"
            }
          },
          {
            "actor": {
              "name": "李俊濠"
            }
          },
          {
            "actor": {
              "name": "劉源"
            }
          },
          {
            "actor": {
              "name": "王子騰"
            }
          }
        ],
        "drama_types": [
          {
            "type_id": 51,
            "type": {
              "name": "大陸劇",
              "label": "category"
            }
          },
          {
            "type_id": 52,
            "type": {
              "name": "大陸",
              "label": "region"
            }
          },
          {
            "type_id": 22,
            "type": {
              "name": "劇情",
              "label": "taxonomy"
            }
          },
          {
            "type_id": 38,
            "type": {
              "name": "勵志",
              "label": "taxonomy"
            }
          },
          {
            "type_id": 95,
            "type": {
              "name": "青春",
              "label": "taxonomy"
            }
          },
          {
            "type_id": 117,
            "type": {
              "name": "網路劇",
              "label": "taxonomy"
            }
          }
        ]
      }
    ]
  }
}
```

## 2.4 分集大綱列表

_進入戲劇詳細頁後，點選下方分頁「分集大綱」，即打此 api 顯示該劇分集大綱。_

_前端規則：當資料不足 10 筆，視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10。_

- 分集大綱 WF [https://whimsical.com/9jvUhuBTdx2HFSt3vtLde9]

- Query

```
query {
  episode(limit: 3, where: {drama_id: {_eq: "43"}}) {
    drama_title
    season
    episode_number
    episode_title
    content
    thumbnail
  }
}


```

- Response

```json
{
  "data": {
    "episode": [
      {
        "drama_title": "熱血同行",
        "episode_number": 1,
        "episode_title": "崇利明初遇阿易讚賞有加 崇利明支持舒爾泰變法維新",
        "content": "崇利明初遇阿易讚賞有加 崇利明支持舒爾泰變法維新　　據說在清兵入關之初，世祖皇上身邊出現了一支神秘的近衛，護衛天子，功勳赫赫，這支近衛部隊被命名為“艷勢番”，歷經百年之後，帝位更替，艷勢番始終存在，入番者皆為八旗名門子弟，表面各有顯赫身份，暗中直接效命於天子，成為了皇權最神秘的護衛者。　　阿易（易烊千璽飾）在很小的時候遭遇變故，他所在的村子被屠，他的家也被燒成灰燼，母親不知去向，於是阿易成了孤兒，一轉眼十三年過去了，阿易和大傻輾轉從關外流亡來到京城，他想要找到失散多年的母親和當初屠村的兇手。　　1908年，正是新舊文化交迭之際，留洋風潮方興未艾，額爾吉·崇利明（黃子韜飾）是滿洲正白旗的貴族，是一位世襲的貝勒爺，他在少年時期留學歐洲，後來到日本進修軍校，如今學成回國，意氣風發，開洋車、穿洋裝、留洋發，是皇城根下有名的新潮人物，青樓花魁芳兒對崇利明情有獨鍾，特意托人從南方帶回來龍鳳喜餅送給他，崇利明將她調侃一番並把隨身的玉墜送給了她。　　賈長安是京城的紈絝子弟，仗著舅舅是步軍統領衙門統領芮臻，便開始飛揚跋扈，這天他調戲馬記羊湯館的晴兒，剛好被阿易撞見，就把賈長安痛打一頓並扔了出去，崇利明正好路過，他對敢打賈長安的人很是好奇，於是走進羊湯館想看看到底是誰。一進門，就看到阿易狼吞虎咽地喝著羊湯，晴兒則走出來向崇利明講述了賈長安調戲她的事。這時，步軍統領衙門的官兵氣勢洶洶來抓阿易，崇利明厲聲喝止，可他們根本不聽，依舊衝上去抓阿易，卻被阿易三拳兩腳打翻在地，為首的官兵拔槍對準阿易，張口誣陷他是亂黨，崇利明搶過手槍，亮出了自己身份，那些人急忙跪地求饒，被崇利明趕了出去。　　崇利明欣賞阿易的功夫和正直的為人，他想要把阿易收入麾下，但阿易卻不領情，對晴兒表示要把吃剩下的羊肉帶走，晴兒免費送給他二斤羊肉和十個燒餅來表示感謝，崇利明則把自己的名帖送給了阿易。大傻以為阿易走丟了，正在家裡痛哭，見到阿易回來後非常高興，他一口氣吃光了阿易帶回來的牛肉和燒餅，他想繼續陪著阿易找母親，可阿易手裡只有一個母親的信物胭脂盒，想要從偌大的京城找到母親，無異於大海撈針。　　太后老佛爺抱病在床久治不愈，太監董連海在一旁小心伺候著，太后忌憚當今皇上翅膀硬了，總想著革新變法，讓董連海派人悄悄去查帝黨名單。崇利明教父親下西洋棋，父親則提醒他不要總去找參與救皇上被革職的舒爾泰，崇利明卻覺得只有皇上才能挽救腐敗沒落的清王朝。次日一早，崇利明就來聽雨軒找舒爾泰，卻被一個不知趣的太監阻攔，崇利明狠狠地打了他一記耳光，董連海急忙任由崇利明出入。崇利明把皇上和太后的脈案交給了舒爾泰，舒爾泰看到了希望，他覺得太后的身體撐不了太久，到時候皇上從贏台出來，他們還可以一起立憲變法。　　賈長安一直偷偷跟蹤著大傻和阿易，二人來到古玩店打聽線索，老闆一眼認出那個胭脂盒是皇宮裡的貢品，這時賈長安帶步軍統領衙門的人突然闖了進來，誣陷阿易和大傻竊取貢品，把他們抓了回去。崇利明參加步軍統領衙門的聚會，太后賞賜了他們一萬兩銀子，統領芮臻趁機規勸崇利明和舒爾泰保持距離，以免被牽連。王公瘟狗偷偷向洋人買軍火，卻遇到了洋人黑吃黑，幸虧他提前進行了準備，帶著司三和華格納裡應外合把洋人全部打死，將軍火全部據為己有。",
d      },
      {
        "drama_title": "熱血同行",
        "episode_number": 2,
        "episode_title": "崇利明再次救下阿易 若婉認定阿易就是真兒",
        "content": "崇利明再次救下阿易 若婉認定阿易就是真兒　　董連海給皇上送飯，看到皇上熟睡，便從他的桌子上偷偷拿走一篇文章交給了太后，太后得知皇上正在研讀孟德斯鳩，氣得大發雷霆，她知道皇上還要堅持變法維新。　　被帶到了衙門的阿易和大傻正被衙差們毆打，副尉楊真走過來制止了他們，楊真以為這又是賈長安公報私仇，帶頭的衙差稱阿易他們昨日毆打官差今天又被查到了私藏貢品。楊真拿著從阿易身上搜到的崇利明名帖詢問賈長安，賈長安並未慌亂，稱這個有可能是阿易他們偷的。楊真說不管怎么樣他還是要告訴貝勒爺一聲，賈長安卻很輕蔑地說他還真拿自己當楊府大少爺了，賈長安走後，楊真從桌子上撿到了一個胭脂盒，正是阿易母親的那個信物。　　楊真拿著名帖找到了崇利明，崇利明得知阿易被賈長安以亂黨的名義抓了，他很是生氣。阿易和大傻被綁了起來，賈長安對阿易侮辱了一番，然後準備嚴刑拷打，這時，崇利明和可顏辛衝進了牢房，崇利明直接上手兩個巴掌打了過去，賈長安滿嘴是血卻只能跪地求饒。崇利明笑著對阿易說自己又救了他一命。　　崇利明帶著阿易和大傻來到了楊真家，吃飯時，崇利明讓楊真腰桿要硬一些，畢竟他也是神機營的人，阿易聽到這話後忙問他們和神機營是什麼關係，可顏辛驕傲地介紹說崇利明是神機營的副都統，這時，有人送來了步軍統領衙門芮臻的信，崇利明看完後讓他們先吃，自己有事需要過去處理一下。　　崇利明在上林仙館跟芮臻會面，芮臻告訴他，五點鐘同盟會的人在這裡接頭，崇利明突然看到了自己在日本認識的周覺走了進來，他意識到周覺應該就是來與同盟會接頭的人。崇利明看到芳兒跳完舞后就上前賞了她一錠銀子並附在她耳邊說了一句話，隨後，芳兒把捧花扔到了周覺手中，她告訴周覺已經暴露了並把他帶到了一個房間內，周覺很是焦急要去通知同僚，芳兒攔住了他，說現在如果他出去，那么他們就都得死並告訴他，是崇利明讓自己救的他。　　楊真和阿易開始拼酒，可顏辛看到他們劍拔弩張的樣子趕緊相勸，但是二人誰都沒有聽他的話，而是直接對瓶吹了一瓶洋酒。阿易喝點有點多了，他跑出去吐了起來，隨後他坐在橋邊想起了可顏辛說崇利明是神機營的人，這讓他心裡很不舒服。醉酒的阿易不小心誤入到了一個房間，他在桌子上看到了和母親的信物一樣的胭脂盒，這時，楊真的母親若婉走了進來，她看到阿易後，直接稱呼他為真兒，阿易拿起了胭脂盒急忙離開，但是若婉衝上前抱住了他不肯鬆手。楊真聽到了聲音趕了過來，拉開若婉的手告訴她，自己才是她的兒子，但若婉卻認定阿易才是她的真兒。可顏辛告訴阿易，這件事其實也不怪楊真，若婉早年間受過刺激，現在還是神志不清的狀態。　　阿易並沒有說什麼，出了楊府後，他拿出了崇利明的名帖讓可顏辛轉交給崇利明，稱自己以後與他再無關係。崇利明回來後得知阿易已經走了很是焦急，接著他質問楊真為什麼要開槍打阿易，楊真解釋說自己只是想嚇唬他一下。楊真看著手裡的胭脂盒不禁回想起自己幼時被領養的場景，他只是楊老爺為了讓若婉開心的工具而已，此時，若婉正在為了自己的胭脂盒而發狂，楊真沒有辦法只好拿出了自己撿到的那個胭脂盒，若婉這才安靜下來。　　芳兒告訴崇利明，周覺已經走了，他給崇利明留下了一個地址，隨後，崇利明帶著楊真和瘟狗來到了雲彩樓找周覺，他說自己明明已經放了他一命，沒想到他還往自己槍口上撞。周覺並未驚慌，只是提起了他們在日本的初次相遇，那時的周覺是革命黨，而崇利明則是到日本留學的公子哥。",
        "thumbnail": "https://hd.itsfun.com.tw/img/f/6d8/wZwpmL2UzVBRTOGFTMxkTMtYTMvcTMxETOx8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      },
      {
        "drama_title": "熱血同行",
        "episode_number": 3,
        "episode_title": "阿易暗中幫忙致崇利明軍火被查 語初與崇利明交鋒先抑後揚",
        "content": "阿易暗中幫忙致崇利明軍火被查 語初與崇利明交鋒先抑後揚　　周覺直言，在日本的時候他就認為崇利明跟別人不一樣，但是他選的路錯了，因為他們的變法維新於國於民而言毫無用處，崇利明表示，自己今天過來不是聽他講道理的，而是要親手抓他，周覺非常痛心地說自己看錯了人。瘟狗把周覺帶到了郊外的一片竹林，接著他把周覺身上的繩子解開了，並稱這是崇利明的意思，讓他以後不要再來京城了，走得越遠越好。　　崇利明將瘟狗帶回來的軍火藏在了楊府，這樣可以省掉不少的麻煩，但是阿易偷聽到了楊真和司三的對話，司三說昨天夜裡崇利明去見周覺了，而崇利明私放了亂黨，他叮囑楊真千萬不要把這件事泄露出去。　　愛新覺羅·語初是步軍統領衙門護軍參領，她也是清朝的格格，此次特意奉哲聿王爺的命令來神機營搜查軍火。就在司三和語初在對峙的時候，崇利明回來了，他說如果沒有搜出走私軍火那么她就要把自己賠給他，語初並未膽怯，爽快地答應下來。司三之前被語初用劍刺傷了手，他說今天自己必須要報仇，而語初的手下什麼都沒搜到，崇利明很是得意，語初直接問他晚上在哪兒見面，崇利明告訴她，晚上八點，上林仙館。　　神機營正在審訊兩個同盟會的人，崇利明看到了他們竟然把女人和孩子帶過來要脅很是生氣，最後崇利明稱有什麼事情自己擔著，這才在芮臻的眼皮底下放走了那對母子。語初告訴自己的舅舅哲聿王爺，在神機營沒有找到軍火，她推斷有可能會藏在了審修的府邸，正好藉機打壓抑一下審修的氣焰，但哲聿王爺並沒有動這個念頭，他向語初說起了艷勢番的來歷和過往，隨後告訴語初要繼續嚴查軍火的事情。　　語初離開王府，發現阿易在後面偷偷地跟蹤，於是她逼迫阿易現身並質問他為什麼跟著自己。阿易什麼也沒說，轉身就跑，語初在後面緊緊跟隨，就這樣她追過了好幾條街，最後來到了一戶人家。語初見到有一扇打開的門，她走進去一看，裡面竟然全是軍火，她馬上意識到，是跟蹤自己的人將她引到了這個地方，而這裡應該就是崇利明藏匿走私軍火的地方。　　上林仙館，語初按照約定前來赴約，可顏辛十分知趣地把司三給帶走了。崇利明本是打算讓她喝一杯就行了，但是語初嫌這裡太吵，於是崇利明把她帶到了樓上雅間，崇利明笑著夸語初這樣穿著很漂亮，語初依舊板著一張臉說自己漂亮不關他的事。與此同時，賈長安和衙門的捕頭帶著手下前去楊府搜查走私軍火，賈長安這次可是奉哲聿王爺之命前來搜查的，他現在根本不懼怕崇利明，手下人把楊真抓了起來。　　可顏辛告訴崇利明，仙兒姑娘請他上去，崇利明聽後馬上開心的轉身要走，語初看到後十分氣憤，她生氣的是崇利明竟然為了一個妓女而拋下了自己。崇利明原來是打算給仙兒贖身，但是仙兒卻屢次拒絕了他，這時，可顏辛告訴他楊府出事了，他們走私的那批軍火被人給抄了。　　芮臻跟崇利明談起了生意，內容就是這批軍火，為了解決這次麻煩，崇利明只好把一挺馬克沁和一萬發子彈送給了他。楊真回到家後卻發現母親若婉走丟了，於是趕緊命人四處尋找，若婉迷迷糊糊走出家門後就漫無目的地走，沒想到被幾個別有用心之人給圍住了，就在他們拖拽若婉的時候，阿易及時出現趕走了那幾個人。若婉被救後就一直拽著阿易的腰帶不肯鬆手，阿易把她送回了楊府，他不願再惹麻煩，隨後轉身離開了。",
        "thumbnail": "https://hd.itsfun.com.tw/img/f/6d8/wZwpmL2UzVBRTOGFTMxkTMtYTMvcTMxETOx8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      }
    ]
  }
}
```

## 2.5 分集大綱詳細

_進入分集大綱列表後，點選任一分集大綱，即打此 api，取得該集大綱詳細頁資訊。_

- Query

```
query {
  episode(where: {drama_id: {_eq: "43"}, episode_number: {_eq: 5}}) {
    drama_title
    season
    episode_number
    episode_title
    content
    thumbnail
  }
}

```

- Response

```json
{
  "data": {
    "episode": [
      {
        "drama_title": "熱血同行",
        "season": 1,
        "episode_number": 5,
        "episode_title": "崇利明設計欲救舒爾泰 舒爾泰捨生取義喝毒酒",
        "content": "崇利明設計欲救舒爾泰 舒爾泰捨生取義喝毒酒　　老馬頭讓晴兒趕緊離開這裡，但是晴兒哭著說自己是不會走的，她說可以找崇利明幫忙。老馬頭哭著說平日裡幫忙那是情分，但是殺人這是死罪不能再給人家添麻煩了。晴兒打算把賈長安的屍體拖出去埋了，但是在路上不小心碰到了司三、楊真和華格納。他們正打算跟晴兒打招呼，但是晴兒一反常態看見他們就逃走，於是他們就上前查看。沒想到拉車上是賈長安的屍體，回到了店裡，老馬頭把事情的經過告訴了他們。華格納問楊真能不能瞞一下，楊真很是為難地說賈長安好歹是一個公差，想要瞞下這個恐怕有點難。隨後華格納問老馬頭賈長安來的時候有人看見嗎，老馬頭惶恐地回答說只有他一個人過來，接著華格納就說自己需要賈長安的屍體一用。等到他們三個人商量完，華格納讓老馬頭一定不能把這件事泄露出去。　　芮臻認為崇利明的話不可全信，畢竟舒爾泰是一手扶持他的人，但是違抗艷勢番的後果他不是不知道，如果他有異心自己只能來硬的了。太后的身體一日不如一日了，而皇上也因為太監們把自己每日的冰場給毀了而氣壞了身子。審修想把崇利明送出京城，因為太后這樣的人十分心狠手辣，但是崇利明認為現在的局勢自己是不可能走的。接著崇利明就提到了艷勢番的密令，審修知道他一定是要救舒爾泰，他認為這就是找死。崇利明問他組建宮廷救火隊的原因，審修說自己那是為了保護皇上，崇利明這才知道自己的父親跟自己的站隊是一樣的。　　崇利明讓瘟狗把自己的車后座給卸了，接著他就讓可顏辛準備一輛車等在指定的地方，會有一個人需要他接到上林仙館的仙兒那裡。崇利明再三囑咐這件事情事關重大，務必不能出錯。原來華格納找屍體的原因是為了偷梁換柱，崇利明打算一把火燒了聽雨軒，到時候賈長安的屍體就是舒爾泰的屍體。上林仙館內，崇利明正跟一個頭上紋身的男子蓮二競爭仙兒的陪酒時間，只要是崇利明出的價錢，蓮二必定多加一兩。最後崇利明拿出了自己的珍藏版手槍，蓮二說他現在是拿官威壓自己，就在這時，可顏辛拿著銀票過來了。　　審修問阿佐崇利明到底要做什麼，阿佐沒辦法只好說出崇利明打算燒聽雨軒的事情，審修一聽大為震怒。崇利明告訴仙兒自己現在要她幫忙做一件事，可能會有殺身之禍，仙兒聽到了很是震驚就想拒絕，但是崇利明說這次她不可以拒絕。審修等到崇利明回來之後告訴他必須連夜出城，崇利明說自己已經沒有回頭路了，他其實還有另外的打算那就是帶著他們殺出去。　　三天的最後一天，崇利明帶著一瓶酒來到了聽雨軒，身後還跟著艷勢番的其他成員。到了舒爾泰那裡，崇利明掏出了槍並且讓他趕緊跟自己出去殺個痛快。舒爾泰讓他遇到事情別自亂陣腳，而後他問了外面的人數，崇利明說現在已經沒有時間了，並且他們兩個人聯手死的不一定是他們。舒爾泰讓崇利明出去確保後門沒有伏兵，可就在崇利明看向窗外的時候，舒爾泰狠下心喝下了毒酒。舒爾泰說自己有他這么個兄弟此生已經無憾了，自己的理想可能無法實現了，他以後還會遇到更多的阻礙，因此他必須學會捨棄。其他艷勢番的人進去查看確保舒爾泰死了，而這時，鐘聲突然響起仿佛是在送逝去的人。與此同時，皇宮裡也已經變天，皇上駕崩。",
        "thumbnail": "https://hd.itsfun.com.tw/img/f/6d8/wZwpmL2UzVBRTOGFTMxkTMtYTMvcTMxETOx8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg"
      }
    ]
  }
}
```


## 2.6 取得演員列表

_用戲劇id取得此戲劇actor list_

- query
```
{
  drama_actor(where: {drama_id: {_eq: "1"}}, limit: 3, order_by: {actor: {count: desc}}) {
    actor {
      name
    }
  }
}

```
- Response
  
```json
{
  "data": {
    "drama_actor": [
      {
        "actor": {
          "name": "陳法蓉"
        }
      },
      {
        "actor": {
          "name": "程硯秋"
        }
      },
      {
        "actor": {
          "name": "蘇祈安"
        }
      }
    ]
  }
}
```


## 2.7 戲劇相關文章列表

_當用戶瀏覽戲劇詳細頁時，打此 api 下方會顯示相關新聞結果列表。_

- Query

```
query {
  drama(where: {title: {_ilike: "%陳情令%"}}, order_by: {created_at: desc}, limit: 3) {
    id
    title
    thumbnail
    excerpt
  }
}

```

- Response

```json
{
  "data": {
    "drama": [
      {
        "id": 9994,
        "title": "魔道祖師：陳情令",
        "thumbnail": "https://img.58b.tv/movieimg/2019-06/5d14cd32271b8.jpg",
        "excerpt": "十六年前，天下五分，姑蘇藍氏，雲夢江氏，清河聶氏，岐山溫氏，蘭陵金氏共治天下。溫氏一家獨大，其餘四家均受其苦。眾家青年中，江氏故人之子魏無羨性格開朗，和以雅正聞名的姑蘇藍氏弟子藍忘機相識並引為知己。一次偶然的機會，二人發現了藍氏一直以來守護的秘密，二人繼承遺志，為蒼生消除隱患。但沒想到一切的幕後黑手正是溫氏家主溫若寒。眾家不堪其辱，合力討伐溫氏。溫氏覆滅後，魏無羨卻為保護溫氏無辜之人不惜與眾家對立，最終被奸人所害釀成大禍，誤害師姐江厭離，自己也不知所蹤。十六年後，消失已久的魏無羨出現在莫家莊，偶遇故人藍忘機。莫家莊一樁樁詭異的兇案顯得撲朔迷離。隨著真相一步步揭開，身處幕後的金光瑤漸漸難以隱藏。最後金光瑤身死，藍忘機承擔起了匡扶天下的使命，而魏無羨不忘初心，最終瀟灑世間。\r\n"
      },
      {
        "id": 8761,
        "title": "魔道祖師：陳情令 特別版",
        "thumbnail": "https://img.58b.tv/movieimg/2019-12/5e04937e75c83.jpg",
        "excerpt": "十六年前，天下五分，姑蘇藍氏，雲夢江氏，清河聶氏，岐山溫氏，蘭陵金氏共治天下。溫氏一家獨大，其餘四家均受其苦。眾家青年中，江氏故人之子魏無羨性格開朗，和以雅正聞名的姑蘇藍氏弟子藍忘機相識並引為知己。一次偶然的機會，二人發現了藍氏一直以來守護的秘密，二人繼承遺志，為蒼生消除隱患。但沒想到一切的幕後黑手正是溫氏家主溫若寒。眾家不堪其辱，合力討伐溫氏。溫氏覆滅後，魏無羨卻為保護溫氏無辜之人不惜與眾家對立，最終被奸人所害釀成大禍，誤害師姐江厭離，自己也不知所蹤。十六年後，消失已久的魏無羨出現在莫家莊，偶遇故人藍忘機。莫家莊一樁樁詭異的兇案顯得撲朔迷離。隨著真相一步步揭開，身處幕後的金光瑤漸漸難以隱藏。最後金光瑤身死，藍忘機承擔起了匡扶天下的使命，而魏無羨不忘初心，最終瀟灑世間。"
      },
      {
        "id": 469,
        "title": "陳情令",
        "thumbnail": "https://hd.itsfun.com.tw/img/3/6e3/nBnauAzMKBzMBFzMGpVMtYTMvMDM3ATOx8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg",
        "excerpt": " \t　　陳情令劇情根據墨香銅臭小說《魔道祖師》改編，以五大家族為背景，講述了雲夢江氏故人之子魏無羨和姑蘇藍氏含光君藍忘機重遇，攜手探尋往年真相的故事。\t　　十六年前，天下五分，姑蘇藍氏，雲夢江氏，清河聶氏，岐山溫氏，蘭陵金氏共治天下。溫氏一家獨大，其餘四家均受其苦。眾家青年中，江氏故人之子魏無羨性格開朗，和以雅正聞名的姑蘇藍氏弟子藍忘機相識並引為知己。\t　　一次偶然的機會，二人發現了藍氏一直以來守護的秘密，二人繼承遺志，為蒼生消除隱患。但沒想到一切的幕後黑手正是溫氏家主溫若寒。眾家不堪其辱，合力討伐溫氏。溫氏覆滅後，魏無羨卻為保護溫氏無辜之人不惜與眾家對立，最終被奸人所害釀成大禍，誤害師姐江厭離，自己也不知所蹤。\t　　十六年後，消失已久的魏無羨在莫家莊出現，偶遇故人藍忘機。莫家莊一樁樁詭異的兇案顯得撲朔迷離。隨著真相一步步揭開，身處幕後的金光瑤漸漸難以隱藏。最後金光瑤身死，藍忘機承擔起了匡扶天下的使命，而魏無羨不忘初心，最終瀟灑世間。 "
      }
    ]
  }
}
```

## 2.8 戲劇相關戲劇列表

_打api2.6取得演員list之後再用回傳的演員名做 or query_

- query
```
query {
    drama(where: {drama_actors: {_or: [
    {actor: {name: {_eq: "陳法蓉"}}},
    {actor: {name: {_eq: "蘇祈安"}}},
    {actor: {name: {_eq: "程硯秋"}}}
    ]}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    thumbnail
    year
    drama_actors(order_by: {actor: {count: desc}}) {
      actor {
        name
      }
    }
    drama_types {
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
    "drama": [
      {
        "id": 32864,
        "title": "秋香怒點唐伯虎(國語)",
        "thumbnail": "https://img.58b.tv/movieimg/2010-11/4cd422edcb3ce.jpg",
        "year": 2010,
        "drama_actors": [
          {
            "actor": {
              "name": "陳豪"
            }
          },
          {
            "actor": {
              "name": "胡杏兒"
            }
          },
          {
            "actor": {
              "name": "夏雨"
            }
          },
          {
            "actor": {
              "name": "黎諾懿"
            }
          },
          {
            "actor": {
              "name": "陳法蓉"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "港劇",
              "label": "category"
            }
          },
          {
            "type": {
              "name": "香港",
              "label": "region"
            }
          }
        ]
      },
      {
        "id": 31299,
        "title": "為你燃燒",
        "thumbnail": "https://img.58b.tv/movieimg/2013-07/51de17c84b976.jpg",
        "year": 2004,
        "drama_actors": [
          {
            "actor": {
              "name": "顏丹晨"
            }
          },
          {
            "actor": {
              "name": "馬景濤"
            }
          },
          {
            "actor": {
              "name": "錢泳辰"
            }
          },
          {
            "actor": {
              "name": "陳法蓉"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "陸劇",
              "label": "category"
            }
          },
          {
            "type": {
              "name": "倫理",
              "label": "taxonomy"
            }
          },
          {
            "type": {
              "name": "大陸",
              "label": "region"
            }
          },
          {
            "type": {
              "name": "劇情",
              "label": "taxonomy"
            }
          },
          {
            "type": {
              "name": "情感",
              "label": "taxonomy"
            }
          }
        ]
      },
      {
        "id": 29360,
        "title": "追日者",
        "thumbnail": "https://img.58b.tv/movieimg/2014-08/53dae799d2ddc.jpg",
        "year": 1993,
        "drama_actors": [
          {
            "actor": {
              "name": "宣萱"
            }
          },
          {
            "actor": {
              "name": "張衛健"
            }
          },
          {
            "actor": {
              "name": "鄭則仕"
            }
          },
          {
            "actor": {
              "name": "朱茵"
            }
          },
          {
            "actor": {
              "name": "萬梓良"
            }
          },
          {
            "actor": {
              "name": "陳法蓉"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "港劇",
              "label": "category"
            }
          },
          {
            "type": {
              "name": "香港",
              "label": "region"
            }
          },
          {
            "type": {
              "name": "言情",
              "label": "taxonomy"
            }
          },
          {
            "type": {
              "name": "時裝",
              "label": "taxonomy"
            }
          }
        ]
      }
    ]
  }
}
```
## 2.9 戲劇相關討論列表

_當用戶瀏覽戲劇詳細頁時，打此 api 下方會顯示相關討論結果列表。_

- Query

```
query {
  forum(where: {title: {_ilike: "%陳情令%"}}, order_by: {created_at: desc}, limit: 3) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Response

```json
{
  "data": {
    "drama": [
      {
        "id": 9994,
        "title": "魔道祖師：陳情令",
        "thumbnail": "https://img.58b.tv/movieimg/2019-06/5d14cd32271b8.jpg",
        "excerpt": "十六年前，天下五分，姑蘇藍氏，雲夢江氏，清河聶氏，岐山溫氏，蘭陵金氏共治天下。溫氏一家獨大，其餘四家均受其苦。眾家青年中，江氏故人之子魏無羨性格開朗，和以雅正聞名的姑蘇藍氏弟子藍忘機相識並引為知己。一次偶然的機會，二人發現了藍氏一直以來守護的秘密，二人繼承遺志，為蒼生消除隱患。但沒想到一切的幕後黑手正是溫氏家主溫若寒。眾家不堪其辱，合力討伐溫氏。溫氏覆滅後，魏無羨卻為保護溫氏無辜之人不惜與眾家對立，最終被奸人所害釀成大禍，誤害師姐江厭離，自己也不知所蹤。十六年後，消失已久的魏無羨出現在莫家莊，偶遇故人藍忘機。莫家莊一樁樁詭異的兇案顯得撲朔迷離。隨著真相一步步揭開，身處幕後的金光瑤漸漸難以隱藏。最後金光瑤身死，藍忘機承擔起了匡扶天下的使命，而魏無羨不忘初心，最終瀟灑世間。\r\n"
      },
      {
        "id": 8761,
        "title": "魔道祖師：陳情令 特別版",
        "thumbnail": "https://img.58b.tv/movieimg/2019-12/5e04937e75c83.jpg",
        "excerpt": "十六年前，天下五分，姑蘇藍氏，雲夢江氏，清河聶氏，岐山溫氏，蘭陵金氏共治天下。溫氏一家獨大，其餘四家均受其苦。眾家青年中，江氏故人之子魏無羨性格開朗，和以雅正聞名的姑蘇藍氏弟子藍忘機相識並引為知己。一次偶然的機會，二人發現了藍氏一直以來守護的秘密，二人繼承遺志，為蒼生消除隱患。但沒想到一切的幕後黑手正是溫氏家主溫若寒。眾家不堪其辱，合力討伐溫氏。溫氏覆滅後，魏無羨卻為保護溫氏無辜之人不惜與眾家對立，最終被奸人所害釀成大禍，誤害師姐江厭離，自己也不知所蹤。十六年後，消失已久的魏無羨出現在莫家莊，偶遇故人藍忘機。莫家莊一樁樁詭異的兇案顯得撲朔迷離。隨著真相一步步揭開，身處幕後的金光瑤漸漸難以隱藏。最後金光瑤身死，藍忘機承擔起了匡扶天下的使命，而魏無羨不忘初心，最終瀟灑世間。"
      },
      {
        "id": 469,
        "title": "陳情令",
        "thumbnail": "https://hd.itsfun.com.tw/img/3/6e3/nBnauAzMKBzMBFzMGpVMtYTMvMDM3ATOx8ibj5SYidmbpFXdq5yZtl2LvoDc0RHa.jpg",
        "excerpt": " \t　　陳情令劇情根據墨香銅臭小說《魔道祖師》改編，以五大家族為背景，講述了雲夢江氏故人之子魏無羨和姑蘇藍氏含光君藍忘機重遇，攜手探尋往年真相的故事。\t　　十六年前，天下五分，姑蘇藍氏，雲夢江氏，清河聶氏，岐山溫氏，蘭陵金氏共治天下。溫氏一家獨大，其餘四家均受其苦。眾家青年中，江氏故人之子魏無羨性格開朗，和以雅正聞名的姑蘇藍氏弟子藍忘機相識並引為知己。\t　　一次偶然的機會，二人發現了藍氏一直以來守護的秘密，二人繼承遺志，為蒼生消除隱患。但沒想到一切的幕後黑手正是溫氏家主溫若寒。眾家不堪其辱，合力討伐溫氏。溫氏覆滅後，魏無羨卻為保護溫氏無辜之人不惜與眾家對立，最終被奸人所害釀成大禍，誤害師姐江厭離，自己也不知所蹤。\t　　十六年後，消失已久的魏無羨在莫家莊出現，偶遇故人藍忘機。莫家莊一樁樁詭異的兇案顯得撲朔迷離。隨著真相一步步揭開，身處幕後的金光瑤漸漸難以隱藏。最後金光瑤身死，藍忘機承擔起了匡扶天下的使命，而魏無羨不忘初心，最終瀟灑世間。 "
      }
    ]
  }
}
```
---

# 3. 討論區

## 3.1 討論列表頁

_進入討論首頁時，打此 api，即顯示討論最新列表。_

_前端規則：當資料不足 10 筆（戲劇為 15 筆），視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 為 10（戲劇 offset：15）。_

- 討論 WF [https://whimsical.com/JFAQ65FCGBdjmua5EDxENp]


- Query [美劇]

```
query {
  forum(where: {forum_types: {type: {name: {_eq: "美劇"}}}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Query [陸劇]

```
query {
  forum(where: {forum_types: {type: {name: {_eq: "陸劇"}}}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Query [韓劇]

```
query {
  forum(where: {forum_types: {type: {name: {_eq: "韓劇"}}}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Query [日劇]

```
query {
  forum(where: {forum_types: {type: {name: {_eq: "日劇"}}}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Query [台劇]

```
query {
  forum(where: {forum_types: {type: {name: {_eq: "台劇"}}}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Response

```json
{
  "data": {
    "forum": [
      {
        "id": 156,
        "title": "轉：還以為是Netflix呢",
        "created_at": "2020-03-03T16:44:44.07",
        "thumbnail": null,
        "author": {
          "username": "Dcard",
          "image_profile": null
        }
      },
      {
        "id": 162,
        "title": "#文長 我的一二月片單✨💫(Netflix)",
        "created_at": "2020-03-02T16:45:19.355",
        "thumbnail": null,
        "author": {
          "username": "Dcard",
          "image_profile": null
        }
      },
      {
        "id": 165,
        "title": "追劇",
        "created_at": "2020-03-02T07:12:24.432",
        "thumbnail": null,
        "author": {
          "username": "Dcard",
          "image_profile": null
        }
      }
    ]
  }
}
```


# 4. 關鍵字 
## 4.1 熱門關鍵字列表
_用戶點選搜尋後，打此 api ，即顯示近期熱門搜尋關鍵字，用戶可點選任一關鍵字進行搜尋。_

- 搜尋 WF [https://whimsical.com/6yDEHPB1YTN3Q8T9FU6Gop]

- query 

```
query {
  trend(limit: 3, order_by: {count: desc}) {
    id
    name
    count
  }
}

```

- Response

```json
{
  "data": {
    "trend": [
      {
        "id": 1,
        "name": "Justice",
        "count": 5
      },
      {
        "id": 3,
        "name": "VIP",
        "count": 4
      },
      {
        "id": 4,
        "name": "Watcher",
        "count": 3
      },
    ]
  }
}
```


# 5. 搜尋結果
## 5.1 關鍵字/Tag搜尋
_用戶直接在 search bar 關鍵字，點選送出，即可依據關鍵字顯示結果列表。_

_用戶點選新聞詳細頁的 Tag 後，即可打此 api，即可依據 Tag顯示結果列表。_

- 關鍵字/ Tag 搜尋 WF [https://whimsical.com/6yDEHPB1YTN3Q8T9FU6Gop]


### 新聞

- query 

```
query {
  news(where: {title: {_ilike: "%陳情%"}}, order_by: {created_at: desc}, limit: 3) {
    id
    title
    created_at
    excerpt
    thumbnail
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
        "created_at": "2020-03-02T17:00:34.345501",
        "excerpt": "陳情令沒有更新的日子里我們等的度日如年，每天都期待著下周能早點到來，沒關係，今天已經周末了，只要等周一就可以來到十六年前的高甜部分啦！想想就很期待呢！在沒有更新的日子里，我們的主角們也都發了自己人物的主題曲，好聽自然是不必說了，但里邊的暗藏的小心思，你發現了嗎?",
        "thumbnail": "http://p3.pstatp.com/large/pgc-image/3dfd9f046c4649f1bbe6ce2f7122ed7c?/1.jpg"
      },
      {
        "id": 8,
        "title": "《陳情令》中藍湛胸口的烙印到底是怎麼弄成的？",
        "created_at": "2020-03-02T16:55:57.379519",
        "excerpt": "當年在玄武洞的時候。溫晁看上了綿綿。溫晁的女人王靈嬌看不過眼。就在大家都在對付屠戮玄武的時候拿起了烙鐵去想讓綿綿毀容。當時魏無羨看見了這一幕。看著離綿綿越來越近的烙鐵。魏無羨沖了上去。所以那個烙印就印在了他的胸口上。",
        "thumbnail": "https://ek21.com/news/drama/wp-content/uploads/sites/10/2019/08/48ec8b1e529c4d818f2b9393a3029e0d.jpg"
      },
      {
        "id": 4,
        "title": "陳情少年團成團！團名TUBS，全名是The Untamed Boys – TUBS",
        "created_at": "2020-03-02T16:52:15.412739",
        "excerpt": "2019年夏天的一部爆紅的電視劇《陳情令》相信很多人都看了，里面由肖戰飾演的魏無羨和王一博飾演的藍忘機是一對兒很讓人喜歡的男主，里面其他的演員也都讓人眼前一亮，於斌飾演的溫寧和鄭繁星飾演的藍苑都讓人很喜歡。",
        "thumbnail": "https://p1.pstatp.com/large/pgc-image/1f91025e9f4d434e9284a93ee3a4e61e?/1.jpg"
      }
    ]
  }
}
```
### 戲劇

- query 
```
query {
  drama(where: {drama_actors: {actor: {name: {_ilike: "%肖戰%"}}}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    thumbnail
    year
    drama_actors(order_by: {actor: {count: desc}}) {
      actor {
        name
      }
    }
    drama_types {
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
    "drama": [
      {
        "id": 13207,
        "title": "哦！我的皇帝陛下",
        "thumbnail": "https://img.58b.tv/movieimg/2018-04/5ae07ae209158.jpg",
        "year": 2018,
        "drama_actors": [
          {
            "actor": {
              "name": "肖戰"
            }
          },
          {
            "actor": {
              "name": "趙露思"
            }
          },
          {
            "actor": {
              "name": "谷嘉誠"
            }
          },
          {
            "actor": {
              "name": "伍嘉成"
            }
          },
          {
            "actor": {
              "name": "彭楚粵"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "陸劇",
              "label": "category"
            }
          },
          {
            "type": {
              "name": "大陸",
              "label": "region"
            }
          },
          {
            "type": {
              "name": "古裝",
              "label": "taxonomy"
            }
          }
        ]
      },
      {
        "id": 12930,
        "title": "哦！我的皇帝陛下2",
        "thumbnail": "https://img.58b.tv/movieimg/2018-04/5ae07ae209158.jpg",
        "year": 2020,
        "drama_actors": [
          {
            "actor": {
              "name": "肖戰"
            }
          },
          {
            "actor": {
              "name": "趙露思"
            }
          },
          {
            "actor": {
              "name": "谷嘉誠"
            }
          },
          {
            "actor": {
              "name": "伍嘉成"
            }
          },
          {
            "actor": {
              "name": "彭楚粵"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "陸劇",
              "label": "category"
            }
          },
          {
            "type": {
              "name": "大陸",
              "label": "region"
            }
          },
          {
            "type": {
              "name": "古裝",
              "label": "taxonomy"
            }
          }
        ]
      },
      {
        "id": 9994,
        "title": "魔道祖師：陳情令",
        "thumbnail": "https://img.58b.tv/movieimg/2019-06/5d14cd32271b8.jpg",
        "year": 2019,
        "drama_actors": [
          {
            "actor": {
              "name": "宣璐"
            }
          },
          {
            "actor": {
              "name": "孟子義"
            }
          },
          {
            "actor": {
              "name": "李若彤"
            }
          },
          {
            "actor": {
              "name": "肖戰"
            }
          },
          {
            "actor": {
              "name": "王一博"
            }
          }
        ],
        "drama_types": [
          {
            "type": {
              "name": "陸劇",
              "label": "category"
            }
          },
          {
            "type": {
              "name": "大陸",
              "label": "region"
            }
          },
          {
            "type": {
              "name": "古裝",
              "label": "taxonomy"
            }
          },
          {
            "type": {
              "name": "劇情",
              "label": "taxonomy"
            }
          }
        ]
      }
    ]
  }
}
```
### 討論

- query
```
query {
  forum(where: {title: {_ilike: "%陳情%"}}, order_by: {created_at: desc}, limit: 3) {
    id
    title
    created_at
    thumbnail
    author {
      username
      image_profile
    }
  }
}

```

- Response
```json
{
  "data": {
    "forum": [
      {
        "id": 84,
        "title": "陳情令 時時思君，以追來日（藍思追feat.金凌）",
        "created_at": "2020-03-03T06:23:38.994",
        "thumbnail": null,
        "author": {
          "username": "Dcard",
          "image_profile": null
        }
      },
      {
        "id": 477,
        "title": "[閒聊] 《陳情令》陳情令那些小事 (雷)",
        "created_at": "2020-02-29T17:39:03",
        "thumbnail": null,
        "author": {
          "username": "Ptt",
          "image_profile": null
        }
      },
      {
        "id": 481,
        "title": "[閒聊] 陳情令-先看劇再看小說的好處",
        "created_at": "2020-02-28T22:22:36",
        "thumbnail": null,
        "author": {
          "username": "Ptt",
          "image_profile": null
        }
      }
    ]
  }
}
```

## 5.2篩選搜尋
_用戶在戲劇區時，可選擇以類型、地區進行篩選相關戲劇，篩選完畢即可打此 api，更新戲劇列表資料。_

_前端規則：當資料不足 15 筆時，視為最後一頁。進入畫面第一次打此 api，offset 預設為 0，當用戶 load more 時，offset 15。_

- 篩選結果 WF [https://whimsical.com/4WBuD65bkGkLVhESwb4pY1]

- Query
```
query {
  drama(where: {drama_types: {_or: [
  {type: {label: {_eq: "taxonomy"}, name: {_eq: "熱血"}}},
  {type: {label: {_eq: "region"}, name: {_eq: "中國"}}}
  ]}}, limit: 3, order_by: {created_at: desc}) {
    id
    title
    thumbnail
  }
}
```

- Response 

```json
{
  "data": {
    "drama": [
      {
        "id": 30713,
        "title": "火力少年王 真人版 第1季",
        "thumbnail": "https://img.58b.tv/movieimg/2010-11/4cd41b2876c2e.jpg"
      },
      {
        "id": 30703,
        "title": "火力少年王 真人版 第2季",
        "thumbnail": "https://img.58b.tv/movieimg/2014-03/5330ad5117633.jpg"
      },
      {
        "id": 30704,
        "title": "火力少年王真人版 第4季：舞動火力/火力少年王",
        "thumbnail": "https://img.58b.tv/movieimg/2011-09/4e6f7b661f578.jpg"
      }
    ]
  }
}
```
---