```sql
INSERT

  INTO TABLE bi_live.activity_comp_track PARTITION (log_date = '20211223')

SELECT

  *

FROM

  (

  SELECT

    get_json_object(msg, '$.name') as name,

    get_json_object(msg, '$.actId') as act_id,

    get_json_object(msg, '$.spm_id') as spm_id,

    get_json_object(msg, '$.event_type') as type,

    get_json_object(msg, '$.url') as url,

    get_json_object(msg, '$.platform') as platform,

    event_id,

    event_time,

    event_timestamp,

    get_json_object(msg, '$.extend1') as extend1,

    get_json_object(msg, '$.extend2') as extend2,

    get_json_object(msg, '$.extend3') as extend3

FROM

	bili_live.dwd_live_module_view_d

WHERE

 log_date = '20211223'

 and event_id = 'activity.comp.exp'

  ) t
```

