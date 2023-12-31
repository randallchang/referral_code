#
## Update event copywriting by id

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Backend-URL:** `https://{{Base-URL}}/v1/referralEvent/{id}/copywriting`

**Type:** `PUT`

**Description:** Update event copywriting by id.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Backend-Request-headers:**

| Header     | Type   | Required | Description |
|------------|--------|----------|-------------|
| x-operator | string | true     | operator    |

**Body-parameters:**

| Parameter | Type   | Max Length | Required | Description |
|-----------|--------|------------|----------|-------------|
| startTime | int    | -          | true     | startTime   |
| endTime   | string | -          | true     | endTime     |
| startTime | int    | -          | true     | startTime   |
| endTime   | string | -          | true     | endTime     |

**Request-example:**
```
curl -X PUT \
    -H 'Content-Type: application/json' \
    -H 'x-operator: jko_bot' \
    -i https://{{Base-URL}}/v1/referralEvent/1/copywriting --data '
    [
        {
            "startTime": "2024-01-01T00:00:00+08:00",
            "endTime": "2024-07-01T00:00:00+08:00",
            "item": "SUBTITLE",
            "content": "邀請朋友加入獲得 $%s 街口幣"
        },
        {
            "startTime": "2024-01-01T00:00:00+08:00",
            "endTime": "2024-07-01T00:00:00+08:00",
            "item": "DETAIL",
            "content": "{\"key\":\"value\"}"
        }
    ]'
```

**Response-fields:**

| Field              | Type   | Required | Description    |
|--------------------|--------|----------|----------------|
| Result             | string | true     | result code    |
| Message            | string | true     | result message |
| ResultObject       | object | true     | result data    |
| └─content          | array  | true     | content        |
| &emsp;└──startTime | int    | true     | startTime      |
| &emsp;└──endTime   | string | true     | endTime        |
| &emsp;└──item      | string | true     | item           |
| &emsp;└──content   | string | true     | content        |

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
                "item": "SUBTITLE",
                "content": "邀請朋友加入獲得 $%s 街口幣"
            },
            {
                "startTime": "2024-01-01T00:00:00+08:00",
                "endTime": "2024-07-01T00:00:00+08:00",
                "item": "DETAIL",
                "content": "{\"key\":\"value\"}"
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