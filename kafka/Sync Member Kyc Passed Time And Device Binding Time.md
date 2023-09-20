#
## Sync member kyc passed time and device binding time

**sit-bootstrap-servers:** `ka1.jkopay.app:9093,ka2.jkopay.app:9093,ka3.jkopay.app:9093`

**prod-bootstrap-servers:** `kafka-07.jkopay.prod:9093,kafka-08.jkopay.prod:9093,kafka-09.jkopay.prod:9093,kafka-10.jkopay.prod:9093,kafka-11.jkopay.prod:9093,kafka-12.jkopay.prod:9093`

**topic:** `rd4_referral_member`

**Description:** Sync member kyc passed time and device binding time.

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Message-content-type:** `JSON`

**Message-parameters:**

| Parameter     | Type   | Max Length | Required | Description                                                                                 |
|---------------|--------|------------|----------|---------------------------------------------------------------------------------------------|
| type          | string | -          | true     | [ENUM: REFERRAL, KYC_PASS, DEVICE_BIND]                                                     |
| jkosId        | string | -          | true     | jkosId                                                                                      |
| jkosAccountId | string | -          | true     | jkosAccountId                                                                               |
| phoneNumber   | string | -          | false    | phone number                                                                                |
| referralCode  | string | -          | false    | referral code                                                                               |
| eventTime     | string | -          | false    | KYC passed time or device binding time(ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00) |

**Message-example:**
```
{
    "type": "REFERRAL",
    "content": {
        "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45",
        "jkosAccountId": "9001234",
        "phoneNumber": "0912345678",
        "referralCode": "JKOOLAOLA"
    }
}
```
```
{
    "type": "KYC_PASS",
    "content": {
        "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45",
        "eventTime": "2023-08-30T00:00:00+08:00"
    }
}
```
```
{
    "type": "DEVICE_BIND",
    "content": {
        "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45",
        "eventTime": "2023-08-30T00:00:00+08:00"
    }
}

```