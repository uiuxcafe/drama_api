# 2. 登入

## 2.1 Request Authtoken 請求通行碼 [A1]

_用戶需先向 CHT 會員平台申請通行碼後，用戶進入 登入頁 時，打此 API 由 server向會員平台取得登入通行碼。_ 

- API :
  
  `Post` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/RequestAuthtoken

- Param
  
    | 參數 | 敘述 | 資料型態 | 必填 |
    | -- | -- | -- | -- | 
    | authtoken| 通行碼 <li>第一次：帶空值</li><li>自動登入：帶入儲存的通行碼</li>| string | Y |
    | otpw| 自動登入時回傳的欄位 | string | Y |

- <span style="background-color:#007799;">Example Request [To App Server]</span> [初次登入]
  
```json
{ 
    "authtoken":""
}
```

- <span style="background-color:#007799;">Example Request [To App Server]</span> [自動登入]
  
```json
{ 
    "authtoken":"tokenb5d409d9f01f91ca56a259f665eb7d14",
}
```

- <span style="background-color:#007799;">Example Response : [From App Server]</span>[初次登入]
  
```json
{
    "code": "0",
    "message": "OK",
    "authtoken": "tokenb5d409d9f01f91ca56a259f665eb7d14"
}
```

- <span style="background-color:#007799;">Example Response : [From App Server]</span>[自動登入]
  
```json
{
    "code": "0",
    "message": "OK",
    "authtoken": "tokenb5d409d9f01f91ca56a259f665eb7d14",
    "otpw": "autologin15ae9377c92fed0a33feb86fe48156f3"
}
```

以下錯誤代碼為 App Server 回應此 api request 所發出的 response，所有錯誤代碼請⾒本⽂件最後⽅。

- Error Code :

    | 錯誤代碼         | 內容         |
    | ----------- | ----------- |
    | -91 | 資料輸入錯誤 |
    | -92 | 檢查碼錯誤 |
    | -93 | 配發token失敗 |
    | -94 | IP錯誤 |
    | -95 | 自動登入認證碼無效 (會重新配發登入通行碼) |
    | -96 | 自動登入認證碼超過期限 |
    | -97 | 會員修改過帳號或密碼 |
    | -99 | 其它錯誤 |

---

## 2.2 Verify Authorize 授權認證 [A2]

_用戶取得通行碼後，進入登入頁面輸入帳號、密碼與通行碼後，打此 API 進行會員登入認證。_ 
_帳號與密碼需加密：https://www.devglan.com/online-tools/aes-encryption-decryption_

- API :
  
  `Post` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/verify

- Param
  
    | 參數 | 敘述 | 資料型態 | 必填 |
    | -- | -- | -- | -- | 
    | authtoken| 認證碼(認證成功後可應用於自動登入流程) | string | Y |
    | uid| CHT 會員帳號 [需加密] | string | Y |
    | pw| CHT 會員密碼 [需加密] | string | Y |

- <span style="background-color:#007799;">Example Request [To App Server]</span>

```json
{
    "authtoken":"tokenb5d409d9f01f91ca56a259f665eb7d14",
    "uid":"J9XydjOFcQuZuz5bW26X7w==",
    "pw":"kzpWPF4FYPSTSojb63TAGg=="
}
```

- <span style="background-color:#007799;">Example Response : [From App Server]</span>
  
```json
{
    "code": "0",
    "message": "OK",
    "otpw": "autologin15ae9377c92fed0a33feb86fe48156f3"
}
```

以下錯誤代碼為 App Server 回應此 api request 所發出的 response，所有錯誤代碼請⾒本⽂件最後⽅。

- Error Code :

    | 錯誤代碼         | 內容         |
    | ----------- | ----------- |
    |  -91 | 資料輸入錯誤 |
    |  -92 | 檢查碼錯誤 |
    |  -93 | 認證帳號密碼失敗 |
    |  -94 | IP錯誤 |
    |  -95 | 登入通行碼無效 |
    |  -96 | 自動登入認證碼超過期限 |
    |  -99 | 其它錯誤 |
    | 1032 | 此帳號因連續登入錯誤多次，已暫時被鎖定，等待一段時間可再登入。 |
    | 1033 | 此IP因連續登入錯誤多次，已暫時被鎖定，等待一段時間可再登入。 |
    | 1100 | 此IP被列入黑名單，無法登入，需由會員系統管理人員解鎖。 |
    | 1112 | 此帳號被列入黑名單，無法登入，需由客服中心人員解鎖。(帳號黑名單) |
    | 2105 | 此帳號被列入不安全帳號名單，可由會員中心網頁登入後進行認證解鎖。 |

---

## 2.3 Login 授權登入 [A3]

_客戶端(Client)傳送 OTPW 給後端系統作登入授權。授權後，回傳會員授權資料，登入成功的同時，儲存 "authtoken" 資料。_ 

- API :
  
  `Post` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/login

- Param
  
    | 參數 | 敘述 | 資料型態 | 必填 |
    | -- | -- | -- | -- |
    | sn| 會員編號| string | Y |
    | visa| 會員是否曾經登入過此頻道：有=true，無=flase | boolean | Y |
    | usertype| 會員卡別 (common、platinum)| string | Y |
    | cmtime| 會員修改基本資料時間| string | Y |
    | pmtime| 會員修改頻道資料時間| string | Y |

- <span style="background-color:#007799;">Example Request [To App Server]</span>

```json
{
    "otpw":"123456"
}
```

- <span style="background-color:#007799;">Example Response : [From App Server]</span>
  
```json
{
    "code": "0",
    "message": "OK",
    "content":[
        {
            "user_sn":"251914421",
            "visa": true,
            "usertype":"common",
            "cmtime":"2018-04-10T00:13:49Z",
            "pmtime":"2018-04-10T00:13:49Z"
        }
    ]
}
```

## 2.4 Logout 登出 [A4]

_登出時打此 api，同時也清除 cookie_ 

- API :
  
  `Get` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/logout

- <span style="background-color:#007799;">Example Response : [From App Server]</span>
  
```json
{
    "code": "0",
    "message": "OK"
}
```

## 2.5 Keyless 登入

_若用戶無法自動登入的話，再打此 api 採用 keyless 登入，登入成功的同時，儲存 "token" 資料。_ 

- API :
  
  `Post` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/keylesslogin

- <span style="background-color:#007799;">Example Request [To App Server]</span>

```json
{
    "ip":"123.194.176.64"
}
```

- <span style="background-color:#007799;">Example Response : [From App Server]</span>
  
```json
{
    "code": "0",
    "message": "OK",
    "content":[
        {
            "status":"success",
            "time":"2019-09-04 16:32:39",
            "data":{
            "insert_time":"2019-09-04 16:32:39",
            "expire_time":"2019-09-04 17:32:39",
            "line_info":{
                "type":"mobile",
                "number":"0919348938",
                "carrier":"cht",
                "rate":"4G",
                "plan":""
            },
            "contractor_info":{
                "type":"juristic_person",
                "hash_id":"7f7992518adc4cd29a29a17d7a98044404239daae0d64e7c59c2d1a9057ec800"
            },
            "member_info":{
                "sn":251914421,
                "actions":["LOGIN"]
                }
            },
            "2factor":[],
            "token":"c43a29302c6612ed61b4c9363405f77edcd856018357be5ad320934dfb447ae3"
        }
    ]   
}
```
- <span style="background-color:#FF0000;">Example Response : [From App Server]</span> [error code]
  
```json
{
    "code": "500", // 由 kenny 決定
    "message": "IP 反查門號查無資訊", // 平台回傳
    "content":[
        {
            "status":"error",
            "time":"2019-09-04 16:32:39",
            "error":{
                "code":"ERR-LAUTHADM-100001",
                "message":"IP 反查門號查無資訊"
            }
        }
    ]       
}
```

- <span style="background-color:#FF0000;">Example Response : [From App Server]</span> [error code]
  
```json
{
    "code": "500", // 由 kenny 決定
    "message": "IP 錯誤，未授權的來源 IP", // 平台回傳
    "content":[
        {
            "status":"error",
            "time":"2019-09-04 16:32:39",
            "error":{
                "code":"ERR-VALIDATOR-REQ-200001",
                "message":"IP 錯誤，未授權的來源 IP"
            }
        }
    ]       
}
```

- <span style="background-color:#FF0000;">Example Response : [From App Server]</span> [error code]
  
```json
{
    "code": "500", // 由 kenny 決定
    "message": "檢查碼錯誤，檢查碼比對失敗", // 平台回傳
    "content":[
        {
            "status":"error",
            "time":"2019-09-04 16:32:39",
            "error":{
                "code":"ERR-VALIDATOR-REQ-100002",
                "message":"檢查碼錯誤，檢查碼比對失敗"
            }
        }
    ]       
}
```

## 2.6 發送簡訊 OTP

_用戶可使用此 api 發送 OTP 簡訊到用戶的手機上進行驗證登入_ 

- API :
  
  `Post` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/SendOTP

- <span style="background-color:#007799;">Example Request [To App Server]</span>

```json
{
    "mobile":"0919348938"
}
```
- <span style="background-color:#007799;">Example Response [From App Server]</span>

```json
{
    "code": "0",
    "message": "OK",
    "content":[
        {
            "status":"success",
            "time":"2019-09-04 16:32:39"
        }
    ]
}
```

## 2.7 驗證簡訊 OTP

_用戶可使用此驗證登入_

- API :
  
  `Post` <font color=#FFAA33>{{protocol}}</font>://<font color=#FFAA33>{{host}}</font>/api/v1/VerifyOTP

- <span style="background-color:#007799;">Example Request [To App Server]</span>

```json
{
    "mobile":"0919348938",
    "code":"1234"
}
```
- <span style="background-color:#007799;">Example Response : [From App Server]</span>
  
```json
{
    "code": "0",
    "message": "OK",
    "content":[
        {
            "status":"success",
            "time":"2019-09-04 16:32:39",
            "token":"c43a29302c6612ed61b4c9363405f77edcd856018357be5ad320934dfb447ae3",
            "data":{
                "insert_time":"2019-09-04 16:32:39",
                "expire_time":"2019-09-04 17:32:39",
                "line_info":{
                    "type":"mobile",
                    "number":"0919348938",
                    "carrier":"cht",
                    "rate":"4G",
                    "plan":""
                },
                "contractor_info":{
                    "type":"juristic_person",
                    "hash_id":"7f7992518adc4cd29a29a17d7a98044404239daae0d64e7c59c2d1a9057ec800"
                },
                "member_info":{
                    "sn":251914421,
                    "actions":["LOGIN"]
                    }
                },
            "2factor":[{
                "type":"otp",
                "status":"verified", //{unverify, waiting, verified}
                "time":"YYYY-MM-DD HH24:MI:SS"
            }],
            
        }
    ]   
}
```




