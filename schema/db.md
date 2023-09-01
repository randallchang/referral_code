# DB schema

## referral_event:
| column      | Type     | length | nullable | Description                           |
|-------------|----------|--------|----------|---------------------------------------|
| id          | BIGINT   | -      | false    | PK id                                 |
| create_time | DATATIME | -      | false    | create time                           |
| update_time | DATATIME | -      | true     | update time                           |
| type        | VARCHAR  | 20     | true     | event type, [enum:PERSONAL, CAMPAIGN] |
| name        | VARCHAR  | 20     | true     | event name                            |

## referrer:
| column            | Type     | length | nullable | Description                |
|-------------------|----------|--------|----------|----------------------------|
| id                | BIGINT   | -      | false    | PK id                      |
| create_time       | DATATIME | -      | false    | create time                |
| update_time       | DATATIME | -      | true     | update time                |
| referral_event_id | BIGINT   | -      | false    | relative to referral_event |
| referral_source   | VARCHAR  | 128    | false    | in personal case, jkosid   |
| referral_code     | VARCHAR  | 10     | false    | referral code              |

## referral_event_content:
| column                 | Type         | length | nullable | Description                              |
|------------------------|--------------|--------|----------|------------------------------------------|
| id                     | BIGINT       | -      | false    | PK id                                    |
| create_time            | DATATIME     | -      | false    | create time                              |
| update_time            | DATATIME     | -      | true     | update time                              |
| referral_event_id      | BIGINT       | -      | false    | relative to referral_event               |
| start_time             | DATATIME     | -      | false    | start time                               |
| end_time               | DATATIME     | -      | false    | end time                                 |
| referrer_reward_type   | VARCHAR      | 20     | false    | referrer reward type, [ENUM:COIN,COUPON] |
| referrer_reward_amount | DECIMAL(10,2) | -      | false    | referrer reward amount                   |
| referee_reward_type    | VARCHAR      | 20     | false    | referee reward type, [ENUM:COIN,COUPON]  |
| referee_reward_amount  | DECIMAL(10,2) | -      | false    | referee reward amount                    |

## referral_event_copywriting:
| column            | Type     | length | nullable | Description                                                                                   |
|-------------------|----------|--------|----------|-----------------------------------------------------------------------------------------------|
| id                | BIGINT   | -      | false    | PK id                                                                                         |
| create_time       | DATATIME | -      | false    | create time                                                                                   |
| update_time       | DATATIME | -      | true     | update time                                                                                   |
| referral_event_id | BIGINT   | -      | false    | relative to referral_event                                                                    |
| start_time        | DATATIME | -      | false    | start time                                                                                    |
| end_time          | DATATIME | -      | false    | end time                                                                                      |
| item              | VARCHAR  | 20     | false    | item, [ENUM:SUBTITLE,SHARE_MESSAGE,KYC_VALIDATION,<br />EVENT_DETAIL,INVITE_STEPS,REMINDER_MESSAGE] |
| content           | VARCHAR  | 2048   | false    | copywriting content, json string format                                                       |

## referral_event_notify:
| column            | Type     | length | nullable | Description                          |
|-------------------|----------|--------|----------|--------------------------------------|
| id                | BIGINT   | -      | false    | PK id                                |
| create_time       | DATATIME | -      | false    | create time                          |
| update_time       | DATATIME | -      | true     | update time                          |
| referral_event_id | BIGINT   | -      | false    | relative to referral_event           |
| start_time        | DATATIME | -      | false    | start time                           |
| end_time          | DATATIME | -      | false    | end time                             |
| type              | VARCHAR  | 20     | false    | notify type, [ENUM:REFERRER,REFEREE] |
| out_app_title     | VARCHAR  | 100    | false    | out app title                        |
| out_app_content   | VARCHAR  | 2048   | false    | out app content                      |
| in_app_title      | VARCHAR  | 100    | false    | in app title                         |
| in_app_content    | VARCHAR  | 2048   | false    | in app content                       |
| boxed_message     | VARCHAR  | 2048   | false    | boxed message                        |

## referee:
| column           | Type     | length | nullable | Description                          |
|------------------|----------|--------|----------|--------------------------------------|
| id               | BIGINT   | -      | false    | PK id                                |
| create_time      | DATATIME | -      | false    | create time                          |
| update_time      | DATATIME | -      | true     | update time                          |
| referrer_id      | BIGINT   | -      | false    | relative to referrer                 |
| jkos_id          | VARCHAR  | 36     | false    | referee's jkos_id                    |
| phone_number     | VARCHAR  | 10     | false    | referee's phone number               |
| kyc_pass_time    | DATATIME | -      | false    | referee passes kyc time              |
| device_bind_time | DATATIME | -      | false    | referee finishes device binding time |

## referral_reward:
| column        | Type         | length | nullable | Description                                |
|---------------|--------------|--------|----------|--------------------------------------------|
| id            | BIGINT       | -      | false    | PK id                                      |
| create_time   | DATATIME     | -      | false    | create time                                |
| update_time   | DATATIME     | -      | true     | update time                                |
| referrer_id   | BIGINT       | -      | false    | relative to referrer                       |
| referee_id    | BIGINT       | -      | false    | relative to referee                        |
| referral_type | VARCHAR      | 10     | false    | reward to, [ENUM:REFERRER,REFEREE]         |
| reward_type   | VARCHAR      |        | false    | reward type, [ENUM:COIN,COUPON]            |
| reward_amount | DECIMAL(10,2) |        | false    | reward amount                              |
| reward_time   | DATATIME     | -      | false    | reward execution time                      |
| reward_status | VARCHAR      | 10     | false    | reward status, [ENUM:PENDING,SUCCESS,FAIL] |
