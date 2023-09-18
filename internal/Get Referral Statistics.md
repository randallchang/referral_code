#
## Get referral statistics by referrer code id

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Backend-URL:** `https://{{Base-URL}}/v1/referrerCode/{id}/statistics`

**Type:** `GET`

**Description:** Get referral statistics by referrer code id.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Backend-Request-headers:**

| Header     | Type   | Required | Description |
|------------|--------|----------|-------------|
| x-operator | string | true     | operator    |

**Path-parameters:**

| Parameter | Type | Max Length | Required | Description      |
|-----------|------|------------|----------|------------------|
| id        | int  | -          | true     | referrer code id |

note: [Enum description](https://enum_place)

**Request-example:**
```
curl -X GET \
    -H 'x-operator: jko_bot' \
    -i https://{{baseUrl}}/v1/referrerCode/1/statistics
```

**Response-fields:**

| Field                        | Type   | Required | Description                                                                            |
|------------------------------|--------|----------|----------------------------------------------------------------------------------------|
| Result                       | string | true     | result code                                                                            |
| Message                      | string | true     | result message                                                                         |
| ResultObject                 | object | true     | result data                                                                            |
| └─content                    | array  | true     | content                                                                                |
| &emsp;└─jkosAccount          | string | true     | new member jkosAccount                                                                 |
| &emsp;└─phone                | string | true     | new member phone                                                                       |
| &emsp;└─kycPassTime          | string | true     | new member kyc pass time (ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00)         |
| &emsp;└─deviceBindTime       | string | true     | new member device bind time (ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00)      |
| &emsp;└─referralSuccessTime  | string | true     | new member referral success time (ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00) |
| &emsp;└─referrerRewardType   | string | true     | referrer reward type, [ENUM:COIN,COUPON]                                               |
| &emsp;└─referrerRewardAmount | int    | true     | referrer reward amount                                                                 |
| &emsp;└─referrerRewardTime   | string | true     | referrer reward time (ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00)             |
| &emsp;└─referrerRewardStatus | string | true     | referrer reward status, [ENUM:SUCCESS,FAIL]                                           |
| &emsp;└─memberRewardType     | string | true     | member reward type, [ENUM:COIN,COUPON]                                                 |
| &emsp;└─memberRewardAmount   | int    | true     | member reward amount                                                                   |
| &emsp;└─memberRewardTime     | string | true     | member reward time (ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00)               |
| &emsp;└─memberRewardStatus   | string | true     | member reward status, [ENUM:SUCCESS,FAIL]                                             |

note: [Enum description](https://enum_place)

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "content": [
            {
                "jkosAccount": "900416302",
                "phone": "0912345678",
                "kycPassTime": "2023-09-11T16:40:00+08:00",
                "deviceBindTime": "2023-09-11T16:42:00+08:00",
                "referralSuccessTime": "2023-09-11T16:42:00+08:00",
                "referrerRewardType": "COIN",
                "referrerRewardAmount": 200,
                "referrerRewardTime": "2023-09-11T16:43:00+08:00",
                "referrerRewardStatus": "SUCCESS",
                "memberRewardType": "COIN",
                "memberRewardAmount": 200,
                "memberRewardTime": "2023-09-11T16:44:00+08:00",
                "memberRewardStatus": "SUCCESS"
            }
        ]
    }
}
```

**Response-example-special-success(if any):**

None

**Response-example-common-error:**

[See reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/29852060/jkopay-app-svc+result+code)

**Response-example-special-error(if any):**

None