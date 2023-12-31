#
## Check if referral code is valid

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Mobile-URL:** `https://{{Base-URL}}/v1/referralCode/check`

**Backend-URL:** `https://{{Base-URL}}/v1/referralCode/check`

**Type:** `POST`

**Description:** Check if referral code is valid.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Mobile-Request-headers:**

| Header       | Type   | Required | Description  |
|--------------|--------|----------|--------------|
| Authenticate | string | true     | jkopay token |

**Query-parameters:**

| Parameter    | Type   | Required | Description   |
|--------------|--------|----------|---------------|
| referralCode | string | true     | referral code |

**Request-example:**
```
curl -X GET \
    -H 'x-operator: jko_bot' \
    -H 'jkosId': f39719c8-7df9-450c-a83f-2eefdabbf23a' \
    -i https://{{baseUrl}}/v1/referralCode?referralCode=JKO123123
```

**Response-fields:**

| Field        | Type    | Required | Description            |
|--------------|---------|----------|------------------------|
| Result       | string  | true     | result code            |
| Message      | string  | true     | result message         |
| ResultObject | object  | true     | result data            |
| └─isValid    | boolean | true     | is referral code valid |

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "isValid": true
    }
}
```

**Response-example-special-success(if any):**

None

**Response-example-common-error:**

[See reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/29852060/jkopay-app-svc+result+code)

**Response-example-special-error(if any):**

None