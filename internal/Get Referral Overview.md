#
## Get referral overview by jkosAccount

**Base-URL:** [reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/53215233/jkopay-referral-svc+Base-URL+reference)

**Backend-URL:** `https://{{Base-URL}}/v1/referralCode/personal/overview`

**Type:** `GET`

**Description:** Get referral overview by jkosAccount.

**Design review:** [Design Review](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/33424007/referral+code+Design+Review)

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Backend-Request-headers:**

| Header     | Type   | Required | Description |
|------------|--------|----------|-------------|
| x-operator | string | true     | operator    |

**Query-parameters:**

| Parameter   | Type   | Required | Description |
|-------------|--------|----------|-------------|
| jkosAccount | string | true     | jkosAccount |

note: [Enum description](https://enum_place)

**Request-example:**
```
curl -X GET \
    -H 'x-operator: jko_bot' \
    -i https://{{baseUrl}}/v1/referralCode/personal/overview?jkosAccount=9001234
```

**Response-fields:**

| Field                  | Type   | Required | Description                           |
|------------------------|--------|----------|---------------------------------------|
| Result                 | string | true     | result code                           |
| Message                | string | true     | result message                        |
| ResultObject           | object | true     | result data                           |
| └─id                   | int    | true     | referrer code id                      |
| └─byReferrerAccountId  | string | true     | referrer's referrer's jkos account id |
| └─byReferralCode       | string | false    | registration code                     |
| └─referralCode         | string | true     | referral code                         |
| └─referralSuccessCount | int    | true     | referral success count                |
| └─notKycCount          | int    | true     | not kyc count                         |
| └─notDeviceBindCount   | int    | true     | not device bind Count                 |
| └─totalReward          | int    | true     | total reward                          |

note: [Enum description](https://enum_place)

**Response-example:**
```
{
    "Result": "0001",
    "Message": "SUCCESS",
    "ResultObject": {
        "id": 1,
        "byReferrerAccountId": "9001234",
        "byReferralCode": "JKOABCABC",
        "referralCode": "JKOOLAOLA",
        "referralSuccessCount": 5,
        "notKycCount": 1,
        "notDeviceBindCount": 1,
        "totalReward": 1000
    }
}
```

**Response-example-special-success(if any):**

None

**Response-example-common-error:**

[See reference](https://jkopay.atlassian.net/wiki/spaces/RD4/pages/29852060/jkopay-app-svc+result+code)

**Response-example-special-error(if any):**

None