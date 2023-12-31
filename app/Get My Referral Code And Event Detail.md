#
## Get referral code for current user

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Mobile-URL:** `https://{{Base-URL}}/v1/my/referralDetail`

**Backend-URL:** `https://{{Base-URL}}/v1/my/referralDetail`

**Type:** `GET`

**Description:** Get referral code for current user, empty result means user is not eligible now.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Mobile-Request-headers:**

| Header       | Type   | Required | Description  |
|--------------|--------|----------|--------------|
| Authenticate | string | true     | jkopay token |

**Backend-Request-headers:**

| Header | Type   | Required | Description |
|--------|--------|----------|-------------|
| jkosId | string | true     | jkosId      |

**Request-example:**
```
curl -X GET \
    -H 'x-operator: jko_bot' \
    -H 'jkosId': f39719c8-7df9-450c-a83f-2eefdabbf23a' \
    -i https://{{baseUrl}}/v1/my/referralDetail
```

**Response-fields:**

| Field                           | Type   | Required | Description               |
|---------------------------------|--------|----------|---------------------------|
| Result                          | string | true     | result code               |
| Message                         | string | true     | result message            |
| ResultObject                    | object | true     | result data               |
| └─referrerRewardAmount          | int    | true     | referrer reward amount    |
| └─referralTitle                 | string | true     | title or direction        |
| └─referralCode                  | string | true     | referral code             |
| └─referralAction                | object | true     | action for sharing or kyc |
| &emsp;└─text                    | string | true     | router text               |
| &emsp;└─router                  | string | true     | router for sharing or kyc |
| └─eventDetail                   | object | true     | event detail with link    |
| &emsp;└─text                    | string | true     | link text                 |
| &emsp;└─router                  | string | true     | event detail router link  |
| └─steps                         | object | true     | referral steps            |
| &emsp;└─title                   | string | true     | step title                |
| &emsp;└─items                   | array  | true     | items                     |
| &emsp;&emsp;└─title             | string | true     | item title                |
| &emsp;&emsp;└─content           | object | true     | item content              |
| &emsp;&emsp;&emsp;└─styledTexts | array  | true     | styledTexts               |
| &emsp;&emsp;&emsp;&emsp;└─text  | string | true     | text                      |
| &emsp;&emsp;&emsp;&emsp;└─color | string | true     | color                     |
| &emsp;&emsp;&emsp;&emsp;└─style | string | true     | style                     |
| &emsp;&emsp;&emsp;&emsp;└─link  | string | true     | link                      |
| └─footerText                    | string | true     | footerText                |

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "referrerRewardAmount": 200,
        "referralTitle": "我的推薦碼：",
        "referralCode": "JKOOLAOLA",
        "referralAction": {
            "text": "立即分享",
            "router": "jkos://share?text=%E6%96%87%E6%A1%88%E6%96%87%E6%A1%88"
        },
        "eventDetail": {
            "text": "活動詳情",
            "router": "https://mkt.jkopay.com/event/jko_referralcode_info"
        },
        "steps": {
            "title": "邀請三步驟",
            "items": [
                {
                    "title": "步驟一",
                    "content": {
                        "styledTexts": [
                            {
                                "text": "分享註冊碼給尚未註冊街口的朋友",
                                "color": "#000000"
                            }
                        ]
                    }
                },
                {
                    "title": "步驟二",
                    "content": {
                        "styledTexts": [
                            {
                                "text": "朋友於註冊流程中輸入推薦碼，註冊成功後朋友可獲得街口幣",
                                "color": "#000000"
                            },
                            {
                                "text": "300",
                                "color": "#e51400"
                            },
                            {
                                "text": "元",
                                "color": "#000000"
                            }
                        ]
                    }
                },
                {
                    "title": "步驟三",
                    "content": {
                        "styledTexts": [
                            {
                                "text": "每成功推薦 1 位朋友，你也可以獲得街口幣",
                                "color": "#000000"
                            },
                            {
                                "text": "200",
                                "color": "#e51400"
                            },
                            {
                                "text": "元！邀請人數無上限",
                                "color": "#000000"
                            }
                        ]
                    }
                }
            ]
        },
        "footerText": "活動時間：2023/10/10~2024/10/10"
    }
}
```

**Response-example-special-success(if any):**

None

**Response-example-common-error:**

[See reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/29852060/jkopay-app-svc+result+code)

**Response-example-special-error(if any):**

None