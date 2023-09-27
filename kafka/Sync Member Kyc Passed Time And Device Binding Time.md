#
## Sync member kyc passed time and device binding time

**sit-bootstrap-servers:** `ka1.jkopay.app:9093,ka2.jkopay.app:9093,ka3.jkopay.app:9093`

**prod-bootstrap-servers:** `kafka-07.jkopay.prod:9093,kafka-08.jkopay.prod:9093,kafka-09.jkopay.prod:9093,kafka-10.jkopay.prod:9093,kafka-11.jkopay.prod:9093,kafka-12.jkopay.prod:9093`

**topic:** `rd2_registration_member_v1.0`

**Description:** Sync member kyc passed time, device binding time and referral code using.

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Message-content-type:** `JSON`

**Backend-Request-headers:**

| Header         | Type   | Required | Description                             |
|----------------|--------|----------|-----------------------------------------|
| type           | string | true     | [ENUM: REFERRAL, KYC_PASS, DEVICE_BIND] |
| version        | string | true     | start from v1.0                         |
| correlation-id | string | true     | correlation id                          |

**Message-parameters:**

| Parameter    | Type   | Max Length | Required | Description                                                                                 |
|--------------|--------|------------|----------|---------------------------------------------------------------------------------------------|
| referralCode | string | -          | false    | referral code                                                                               |
| eventTime    | string | -          | false    | KYC passed time or device binding time(ISO-8601 time format, ex: 2023-08-30T00:00:00+08:00) |
| phoneNumber  | string | -          | false    | phone number                                                                                |

**Message-example:**
```
type: REFERRAL
version: v1.0
correlation-id: 5a0c10ee-3d48-45cc-9627-a99ec32cca14

{
    "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45",
    "referralCode": "JKOOLAOLA"
}
```

```
type: KYC_PASS
version: v1.0
correlation-id: 5a0c10ee-3d48-45cc-9627-a99ec32cca14

{
    "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45",
    "eventTime": "2023-08-30T00:00:00+08:00",
    "phoneNumber": "0912345678"
}
```

```
type: DEVICE_BIND
version: v1.0
correlation-id: 5a0c10ee-3d48-45cc-9627-a99ec32cca14

{
    "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45",
    "eventTime": "2023-08-30T00:00:00+08:00"
    "phoneNumber": "0912345678"
}

```