#
## Reward Eligible Member and Notify Reward Result

**sit-bootstrap-servers:** `ka1.jkopay.app:9093,ka2.jkopay.app:9093,ka3.jkopay.app:9093`

**prod-bootstrap-servers:** `kafka-07.jkopay.prod:9093,kafka-08.jkopay.prod:9093,kafka-09.jkopay.prod:9093,kafka-10.jkopay.prod:9093,kafka-11.jkopay.prod:9093,kafka-12.jkopay.prod:9093`

**topic:** `rd4_referral_reward_member`

**Description:** Reward eligible member and notify reward result

**PRD:** [RPD](https://jkopay.atlassian.net/wiki/spaces/PM/pages/29687846)

**Message-content-type:** `JSON`

**Backend-Request-headers:**

| Header         | Type   | Required | Description           |
|----------------|--------|----------|-----------------------|
| type           | string | true     | [ENUM: REWARD_MEMBER] |
| version        | string | true     | start from v1.0       |
| correlation-id | string | true     | correlation id        |

**Message-parameters:**

| Parameter | Type   | Max Length | Required | Description |
|-----------|--------|------------|----------|-------------|
| jkosId    | string | -          | true     | jkosId      |

**Message-example:**
```
type: REWARD_ELIGIBLE_MEMBER
version: v1.0
correlation-id: 5a0c10ee-3d48-45cc-9627-a99ec32cca14

{
    "jkosId": "d3b82672-eb20-11ec-b230-00505684fd45"
}
```

.