#
## Update event content by id

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Backend-URL:** `https://{{Base-URL}}/v1/referralEvent/{id}/contents`

**Type:** `PUT`

**Description:** Update event content by id.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Backend-Request-headers:**

| Header     | Type   | Required | Description |
|------------|--------|----------|-------------|
| x-operator | string | true     | operator    |

**Path-parameters:**

| Parameter | Type | Max Length | Required | Description      |
|-----------|------|------------|----------|------------------|
| id        | int  | -          | true     | referrerEvent id |

**Body-parameters:**

| Parameter            | Type   | Max Length | Required | Description                    |
|----------------------|--------|------------|----------|--------------------------------|
| startTime            | int    | -          | true     | startTime                      |
| endTime              | string | -          | true     | endTime                        |
| referrerRewardType   | string | -          | true     | [Enum:COIN] referrerRewardType |
| referrerRewardAmount | string | -          | true     | referrerRewardAmount           |
| memberRewardType     | string | -          | true     | [Enum:COIN] memberRewardType   |
| memberRewardAmount   | string | -          | true     | memberRewardAmount             |

**Request-example:**
```
curl -X PUT \
    -H 'Content-Type: application/json' \
    -H 'x-operator: jko_bot' \
    -i https://{{Base-URL}}/v1/referralEvent/1/contents --data '
    [
        {
            "startTime": "2024-01-01T00:00:00+08:00",
            "endTime": "2024-07-01T00:00:00+08:00",
            "referrerRewardType": "COIN",
            "referrerRewardAmount": 100,
            "memberRewardType": "COIN",
            "memberRewardAmount": 300
        },
        {
            "startTime": "2024-07-01T00:00:00+08:00",
            "endTime": "2024-12-31T00:00:00+08:00",
            "referrerRewardType": "COIN",
            "referrerRewardAmount": 200,
            "memberRewardType": "COIN",
            "memberRewardAmount": 200
        }
    ]'
```

**Response-fields:**

| Field                         | Type   | Required | Description                    |
|-------------------------------|--------|----------|--------------------------------|
| Result                        | string | true     | result code                    |
| Message                       | string | true     | result message                 |
| ResultObject                  | object | true     | result data                    |
| └─content                     | array  | true     | content                        |
| &emsp;└──startTime            | int    | true     | startTime                      |
| &emsp;└──endTime              | string | true     | endTime                        |
| &emsp;└──referrerRewardType   | string | true     | [Enum:COIN] referrerRewardType |
| &emsp;└──referrerRewardAmount | string | true     | referrerRewardAmount           |
| &emsp;└──memberRewardType     | string | true     | [Enum:COIN] memberRewardType   |
| &emsp;└──memberRewardAmount   | string | true     | memberRewardAmount             |

note: [Enum description](https://enum_place)

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "content": [
            {
                "startTime": "2024-01-01T00:00:00+08:00",
                "endTime": "2024-07-01T00:00:00+08:00",
                "referrerRewardType": "COIN",
                "referrerRewardAmount": 100,
                "memberRewardType": "COIN",
                "memberRewardAmount": 300
            },
            {
                "startTime": "2024-07-01T00:00:00+08:00",
                "endTime": "2024-12-31T00:00:00+08:00",
                "referrerRewardType": "COIN",
                "referrerRewardAmount": 200,
                "memberRewardType": "COIN",
                "memberRewardAmount": 200
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