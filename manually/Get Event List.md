#
## Get event list

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Backend-URL:** `https://{{Base-URL}}/v1/referralEvents`

**Type:** `GET`

**Description:** Get event list.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Backend-Request-headers:**

| Header     | Type   | Required | Description |
|------------|--------|----------|-------------|
| x-operator | string | true     | operator    |

**Request-example:**
```
curl -X GET \
    -H 'x-operator: jko_bot' \
    -i https://{{baseUrl}}/v1/referralEvents
```

**Response-fields:**

| Field             | Type   | Required | Description               |
|-------------------|--------|----------|---------------------------|
| Result            | string | true     | result code               |
| Message           | string | true     | result message            |
| ResultObject      | object | true     | result data               |
| └─content         | array  | true     | content                   |
| &emsp;└──id       | int    | true     | referal event id          |
| &emsp;└──type     | string | true     | [Enum:PERSONAL, CAMPAIGN] |
| &emsp;└──name     | string | true     | referal event name        |

note: [Enum description](https://enum_place)

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "content": [
            {
                "id": 1,
                "type": "PERSONAL",
                "name": "好友邀請碼"
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