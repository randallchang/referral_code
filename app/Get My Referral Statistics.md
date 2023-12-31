#
## Get referral statistics

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Mobile-URL:** `https://{{Base-URL}}/v1/my/referrer/statistics`

**Backend-URL:** `https://{{Base-URL}}/v1/my/referrer/statistics`

**Type:** `GET`

**Description:** Get personal referral event statistics.

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
    -i https://{{baseUrl}}/v1/my/referrer/statistics
```

**Response-fields:**

| Field                | Type   | Required | Description                         |
|----------------------|--------|----------|-------------------------------------|
| Result               | string | true     | result code                         |
| Message              | string | true     | result message                      |
| ResultObject         | object | true     | result data                         |
| └─totalReferralCount | int    | true     | registration count by referral code |
| └─totalRewardAmount  | int    | true     | total reward                        |
| └─members            | array  | true     | members, up to 200                  |
| &emsp;└─nickname     | string | true     | nickname (phase 2)                  |
| &emsp;└─image        | string | true     | image (phase 2)                     |
| &emsp;└─phone        | string | true     | phone                               |
| &emsp;└─status       | string | true     | [Enum:INELIGIBLE, ELIGIBLE]         |
| └─reminder           | string | true     | reminder for ineligible members     |

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "ineligibleReferralCount": 2,
        "eligibleReferralCount": 5,
        "totalRewardAmount": 1000,
        "members": [
            {
                "phone": "0912-XXX-461",
                "status": "INELIGIBLE"
            },
            {
                "phone": "0966-XXX-987",
                "status": "INELIGIBLE"
            },
            {
                "phone": "0912-XXX-461",
                "status": "ELIGIBLE"
            },
            {
                "phone": "0912-XXX-461",
                "status": "ELIGIBLE"
            },
            {
                "phone": "0912-XXX-461",
                "status": "ELIGIBLE"
            },
            {
                "phone": "0912-XXX-461",
                "status": "ELIGIBLE"
            },
            {
                "phone": "0912-XXX-461",
                "status": "ELIGIBLE"
            }
        ],
        "reminder": "您的好友已輸入推薦碼，但尚末通過身份驗證。提醒他在 2024/10/10 前完成才可以獲得街口幣獎勵哦！"
    }
}
```

**Response-example-special-success(if any):**

None

**Response-example-common-error:**

[See reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/29852060/jkopay-app-svc+result+code)

**Response-example-special-error(if any):**

None