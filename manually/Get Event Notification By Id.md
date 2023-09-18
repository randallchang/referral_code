#
## Get event notification by id

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Backend-URL:** `https://{{Base-URL}}/v1/referralEvent/{id}/notification`

**Type:** `GET`

**Description:** Get event notification by id.

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
    -i https://{{Base-URL}}/v1/referralEvent/{id}/notification
```

**Response-fields:**

| Field                    | Type   | Required | Description                          |
|--------------------------|--------|----------|--------------------------------------|
| Result                   | string | true     | result code                          |
| Message                  | string | true     | result message                       |
| ResultObject             | object | true     | result data                          |
| └─content                | array  | true     | content                              |
| &emsp;└──startTime       | int    | true     | startTime                            |
| &emsp;└──endTime         | string | true     | endTime                              |
| &emsp;└──notify_type     | string | true     | notify_type, [ENUM:REFERRER,REFEREE] |
| &emsp;└──out_app_title   | string | true     | out_app_title                        |
| &emsp;└──out_app_content | string | true     | out_app_content                      |
| &emsp;└──in_app_title    | string | true     | in_app_title                         |
| &emsp;└──in_app_content  | string | true     | in_app_content                       |
| &emsp;└──boxed_message   | string | true     | boxed_message                        |

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
                "notify_type": "REFERRER",
                "out_app_title": "string",
                "out_app_content": "string",
                "in_app_title": "string",
                "in_app_content": "string",
                "boxed_message": "string"
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