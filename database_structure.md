## テーブル一覧
```
# 接頭語はすべてmatomo_としています。
# matomo_archive_blob_YYYY_MM は年月毎にテーブル追加
# matomo_archive_numeric_YYYY_MM は年月毎にテーブル追加

+---------------------------------------+
| Table List                            |
+---------------------------------------+
| matomo_access                         |
| matomo_archive_blob_YYYY_MM           |
| matomo_archive_numeric_YYYY_MM        |
| matomo_brute_force_log                |
| matomo_goal                           |
| matomo_locks                          |
| matomo_log_action                     |
| matomo_log_conversion                 |
| matomo_log_conversion_item            |
| matomo_log_link_visit_action          |
| matomo_log_profiling                  |
| matomo_log_visit                      |
| matomo_logger_message                 |
| matomo_option                         |
| matomo_plugin_setting                 |
| matomo_privacy_logdata_anonymizations |
| matomo_report                         |
| matomo_report_subscriptions           |
| matomo_segment                        |
| matomo_sequence                       |
| matomo_session                        |
| matomo_site                           |
| matomo_site_setting                   |
| matomo_site_url                       |
| matomo_tagmanager_container           |
| matomo_tagmanager_container_release   |
| matomo_tagmanager_container_version   |
| matomo_tagmanager_tag                 |
| matomo_tagmanager_trigger             |
| matomo_tagmanager_variable            |
| matomo_tracking_failure               |
| matomo_twofactor_recovery_code        |
| matomo_user                           |
| matomo_user_dashboard                 |
| matomo_user_language                  |
+---------------------------------------+
```

## テーブル定義一覧

### matomo_access
```
+----------+------------------+------+-----+---------+----------------+
| Field    | Type             | Null | Key | Default | Extra          |
+----------+------------------+------+-----+---------+----------------+
| idaccess | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| login    | varchar(100)     | NO   | MUL | NULL    |                |
| idsite   | int(10) unsigned | NO   |     | NULL    |                |
| access   | varchar(50)      | YES  |     | NULL    |                |
+----------+------------------+------+-----+---------+----------------+
```

### matomo_archive_blob_2020_05
```
+-------------+---------------------+------+-----+---------+-------+
| Field       | Type                | Null | Key | Default | Extra |
+-------------+---------------------+------+-----+---------+-------+
| idarchive   | int(10) unsigned    | NO   | PRI | NULL    |       |
| name        | varchar(255)        | NO   | PRI | NULL    |       |
| idsite      | int(10) unsigned    | YES  |     | NULL    |       |
| date1       | date                | YES  |     | NULL    |       |
| date2       | date                | YES  |     | NULL    |       |
| period      | tinyint(3) unsigned | YES  | MUL | NULL    |       |
| ts_archived | datetime            | YES  |     | NULL    |       |
| value       | mediumblob          | YES  |     | NULL    |       |
+-------------+---------------------+------+-----+---------+-------+
```

### matomo_archive_numeric_2020_05
```
+-------------+---------------------+------+-----+---------+-------+
| Field       | Type                | Null | Key | Default | Extra |
+-------------+---------------------+------+-----+---------+-------+
| idarchive   | int(10) unsigned    | NO   | PRI | NULL    |       |
| name        | varchar(255)        | NO   | PRI | NULL    |       |
| idsite      | int(10) unsigned    | YES  | MUL | NULL    |       |
| date1       | date                | YES  |     | NULL    |       |
| date2       | date                | YES  |     | NULL    |       |
| period      | tinyint(3) unsigned | YES  | MUL | NULL    |       |
| ts_archived | datetime            | YES  |     | NULL    |       |
| value       | double              | YES  |     | NULL    |       |
+-------------+---------------------+------+-----+---------+-------+
```

### matomo_brute_force_log
```
+--------------------+-------------+------+-----+---------+----------------+
| Field              | Type        | Null | Key | Default | Extra          |
+--------------------+-------------+------+-----+---------+----------------+
| id_brute_force_log | bigint(11)  | NO   | PRI | NULL    | auto_increment |
| ip_address         | varchar(60) | YES  | MUL | NULL    |                |
| attempted_at       | datetime    | NO   |     | NULL    |                |
+--------------------+-------------+------+-----+---------+----------------+
```

### matomo_goal
```
+------------------------+--------------+------+-----+---------+-------+
| Field                  | Type         | Null | Key | Default | Extra |
+------------------------+--------------+------+-----+---------+-------+
| idsite                 | int(11)      | NO   | PRI | NULL    |       |
| idgoal                 | int(11)      | NO   | PRI | NULL    |       |
| name                   | varchar(50)  | NO   |     | NULL    |       |
| description            | varchar(255) | NO   |     |         |       |
| match_attribute        | varchar(20)  | NO   |     | NULL    |       |
| pattern                | varchar(255) | NO   |     | NULL    |       |
| pattern_type           | varchar(25)  | NO   |     | NULL    |       |
| case_sensitive         | tinyint(4)   | NO   |     | NULL    |       |
| allow_multiple         | tinyint(4)   | NO   |     | NULL    |       |
| revenue                | float        | NO   |     | NULL    |       |
| deleted                | tinyint(4)   | NO   |     | 0       |       |
| event_value_as_revenue | tinyint(4)   | NO   |     | 0       |       |
+------------------------+--------------+------+-----+---------+-------+

```

### matomo_locks
```
+-------------+---------------------+------+-----+------------+-------+
| Field       | Type                | Null | Key | Default    | Extra |
+-------------+---------------------+------+-----+------------+-------+
| key         | varchar(70)         | NO   | PRI | NULL       |       |
| value       | varchar(255)        | YES  |     | NULL       |       |
| expiry_time | bigint(20) unsigned | YES  |     | 9999999999 |       |
+-------------+---------------------+------+-----+------------+-------+
```

### matomo_log_action
```
+------------+---------------------+------+-----+---------+----------------+
| Field      | Type                | Null | Key | Default | Extra          |
+------------+---------------------+------+-----+---------+----------------+
| idaction   | int(10) unsigned    | NO   | PRI | NULL    | auto_increment |
| name       | varchar(4096)       | YES  |     | NULL    |                |
| hash       | int(10) unsigned    | NO   |     | NULL    |                |
| type       | tinyint(3) unsigned | YES  | MUL | NULL    |                |
| url_prefix | tinyint(2)          | YES  |     | NULL    |                |
+------------+---------------------+------+-----+---------+----------------+
```

### matomo_log_conversion
```
+--------------------------+----------------------+------+-----+---------+-------+
| Field                    | Type                 | Null | Key | Default | Extra |
+--------------------------+----------------------+------+-----+---------+-------+
| idvisit                  | bigint(10) unsigned  | NO   | PRI | NULL    |       |
| idsite                   | int(10) unsigned     | NO   | MUL | NULL    |       |
| idvisitor                | binary(8)            | NO   |     | NULL    |       |
| server_time              | datetime             | NO   |     | NULL    |       |
| idaction_url             | int(10) unsigned     | YES  |     | NULL    |       |
| idlink_va                | bigint(10) unsigned  | YES  |     | NULL    |       |
| idgoal                   | int(10)              | NO   | PRI | NULL    |       |
| buster                   | int(10) unsigned     | NO   | PRI | NULL    |       |
| idorder                  | varchar(100)         | YES  |     | NULL    |       |
| items                    | smallint(5) unsigned | YES  |     | NULL    |       |
| url                      | varchar(4096)        | NO   |     | NULL    |       |
| visitor_days_since_first | smallint(5) unsigned | YES  |     | NULL    |       |
| visitor_days_since_order | smallint(5) unsigned | YES  |     | NULL    |       |
| visitor_returning        | tinyint(1)           | YES  |     | NULL    |       |
| visitor_count_visits     | int(11) unsigned     | NO   |     | NULL    |       |
| referer_keyword          | varchar(255)         | YES  |     | NULL    |       |
| referer_name             | varchar(70)          | YES  |     | NULL    |       |
| referer_type             | tinyint(1) unsigned  | YES  |     | NULL    |       |
| config_device_brand      | varchar(100)         | YES  |     | NULL    |       |
| config_device_model      | varchar(100)         | YES  |     | NULL    |       |
| config_device_type       | tinyint(100)         | YES  |     | NULL    |       |
| location_city            | varchar(255)         | YES  |     | NULL    |       |
| location_country         | char(3)              | YES  |     | NULL    |       |
| location_latitude        | decimal(9,6)         | YES  |     | NULL    |       |
| location_longitude       | decimal(9,6)         | YES  |     | NULL    |       |
| location_region          | char(3)              | YES  |     | NULL    |       |
| revenue                  | float                | YES  |     | NULL    |       |
| revenue_discount         | float                | YES  |     | NULL    |       |
| revenue_shipping         | float                | YES  |     | NULL    |       |
| revenue_subtotal         | float                | YES  |     | NULL    |       |
| revenue_tax              | float                | YES  |     | NULL    |       |
| custom_var_k1            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_v1            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_k2            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_v2            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_k3            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_v3            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_k4            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_v4            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_k5            | varchar(200)         | YES  |     | NULL    |       |
| custom_var_v5            | varchar(200)         | YES  |     | NULL    |       |
+--------------------------+----------------------+------+-----+---------+-------+
```


### matomo_log_conversion_item
```
+--------------------+---------------------+------+-----+---------+-------+
| Field              | Type                | Null | Key | Default | Extra |
+--------------------+---------------------+------+-----+---------+-------+
| idsite             | int(10) unsigned    | NO   | MUL | NULL    |       |
| idvisitor          | binary(8)           | NO   |     | NULL    |       |
| server_time        | datetime            | NO   |     | NULL    |       |
| idvisit            | bigint(10) unsigned | NO   | PRI | NULL    |       |
| idorder            | varchar(100)        | NO   | PRI | NULL    |       |
| idaction_sku       | int(10) unsigned    | NO   | PRI | NULL    |       |
| idaction_name      | int(10) unsigned    | NO   |     | NULL    |       |
| idaction_category  | int(10) unsigned    | NO   |     | NULL    |       |
| idaction_category2 | int(10) unsigned    | NO   |     | NULL    |       |
| idaction_category3 | int(10) unsigned    | NO   |     | NULL    |       |
| idaction_category4 | int(10) unsigned    | NO   |     | NULL    |       |
| idaction_category5 | int(10) unsigned    | NO   |     | NULL    |       |
| price              | float               | NO   |     | NULL    |       |
| quantity           | int(10) unsigned    | NO   |     | NULL    |       |
| deleted            | tinyint(1) unsigned | NO   |     | NULL    |       |
+--------------------+---------------------+------+-----+---------+-------+
```

### matomo_log_link_visit_action
```
+------------------------------+----------------------+------+-----+---------+----------------+
| Field                        | Type                 | Null | Key | Default | Extra          |
+------------------------------+----------------------+------+-----+---------+----------------+
| idlink_va                    | bigint(10) unsigned  | NO   | PRI | NULL    | auto_increment |
| idsite                       | int(10) unsigned     | NO   | MUL | NULL    |                |
| idvisitor                    | binary(8)            | NO   |     | NULL    |                |
| idvisit                      | bigint(10) unsigned  | NO   | MUL | NULL    |                |
| idaction_url_ref             | int(10) unsigned     | YES  |     | 0       |                |
| idaction_name_ref            | int(10) unsigned     | YES  |     | NULL    |                |
| custom_float                 | float                | YES  |     | NULL    |                |
| server_time                  | datetime             | NO   |     | NULL    |                |
| idpageview                   | char(6)              | YES  |     | NULL    |                |
| interaction_position         | smallint(5) unsigned | YES  |     | NULL    |                |
| idaction_name                | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_url                 | int(10) unsigned     | YES  |     | NULL    |                |
| time_spent_ref_action        | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_event_action        | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_event_category      | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_content_interaction | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_content_name        | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_content_piece       | int(10) unsigned     | YES  |     | NULL    |                |
| idaction_content_target      | int(10) unsigned     | YES  |     | NULL    |                |
| custom_var_k1                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v1                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k2                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v2                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k3                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v3                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k4                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v4                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k5                | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v5                | varchar(200)         | YES  |     | NULL    |                |
+------------------------------+----------------------+------+-----+---------+----------------+
```

### matomo_log_profiling
```
+-------------+---------------------+------+-----+---------+----------------+
| Field       | Type                | Null | Key | Default | Extra          |
+-------------+---------------------+------+-----+---------+----------------+
| query       | text                | NO   | UNI | NULL    |                |
| count       | int(10) unsigned    | YES  |     | NULL    |                |
| sum_time_ms | float               | YES  |     | NULL    |                |
| idprofiling | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
+-------------+---------------------+------+-----+---------+----------------+
```

### matomo_log_visit
```
+---------------------------+----------------------+------+-----+---------+----------------+
| Field                     | Type                 | Null | Key | Default | Extra          |
+---------------------------+----------------------+------+-----+---------+----------------+
| idvisit                   | bigint(10) unsigned  | NO   | PRI | NULL    | auto_increment |
| idsite                    | int(10) unsigned     | NO   | MUL | NULL    |                |
| idvisitor                 | binary(8)            | NO   |     | NULL    |                |
| visit_last_action_time    | datetime             | NO   |     | NULL    |                |
| config_id                 | binary(8)            | NO   |     | NULL    |                |
| location_ip               | varbinary(16)        | NO   |     | NULL    |                |
| user_id                   | varchar(200)         | YES  |     | NULL    |                |
| visit_first_action_time   | datetime             | NO   |     | NULL    |                |
| visit_goal_buyer          | tinyint(1)           | YES  |     | NULL    |                |
| visit_goal_converted      | tinyint(1)           | YES  |     | NULL    |                |
| visitor_days_since_first  | smallint(5) unsigned | YES  |     | NULL    |                |
| visitor_days_since_order  | smallint(5) unsigned | YES  |     | NULL    |                |
| visitor_returning         | tinyint(1)           | YES  |     | NULL    |                |
| visitor_count_visits      | int(11) unsigned     | NO   |     | NULL    |                |
| visit_entry_idaction_name | int(10) unsigned     | YES  |     | NULL    |                |
| visit_entry_idaction_url  | int(11) unsigned     | YES  |     | NULL    |                |
| visit_exit_idaction_name  | int(10) unsigned     | YES  |     | NULL    |                |
| visit_exit_idaction_url   | int(10) unsigned     | YES  |     | 0       |                |
| visit_total_actions       | int(11) unsigned     | YES  |     | NULL    |                |
| visit_total_interactions  | smallint(5) unsigned | YES  |     | 0       |                |
| visit_total_searches      | smallint(5) unsigned | YES  |     | NULL    |                |
| referer_keyword           | varchar(255)         | YES  |     | NULL    |                |
| referer_name              | varchar(70)          | YES  |     | NULL    |                |
| referer_type              | tinyint(1) unsigned  | YES  |     | NULL    |                |
| referer_url               | text                 | YES  |     | NULL    |                |
| location_browser_lang     | varchar(20)          | YES  |     | NULL    |                |
| config_browser_engine     | varchar(10)          | YES  |     | NULL    |                |
| config_browser_name       | varchar(10)          | YES  |     | NULL    |                |
| config_browser_version    | varchar(20)          | YES  |     | NULL    |                |
| config_device_brand       | varchar(100)         | YES  |     | NULL    |                |
| config_device_model       | varchar(100)         | YES  |     | NULL    |                |
| config_device_type        | tinyint(100)         | YES  |     | NULL    |                |
| config_os                 | char(3)              | YES  |     | NULL    |                |
| config_os_version         | varchar(100)         | YES  |     | NULL    |                |
| visit_total_events        | int(11) unsigned     | YES  |     | NULL    |                |
| visitor_localtime         | time                 | YES  |     | NULL    |                |
| visitor_days_since_last   | smallint(5) unsigned | YES  |     | NULL    |                |
| config_resolution         | varchar(18)          | YES  |     | NULL    |                |
| config_cookie             | tinyint(1)           | YES  |     | NULL    |                |
| config_director           | tinyint(1)           | YES  |     | NULL    |                |
| config_flash              | tinyint(1)           | YES  |     | NULL    |                |
| config_gears              | tinyint(1)           | YES  |     | NULL    |                |
| config_java               | tinyint(1)           | YES  |     | NULL    |                |
| config_pdf                | tinyint(1)           | YES  |     | NULL    |                |
| config_quicktime          | tinyint(1)           | YES  |     | NULL    |                |
| config_realplayer         | tinyint(1)           | YES  |     | NULL    |                |
| config_silverlight        | tinyint(1)           | YES  |     | NULL    |                |
| config_windowsmedia       | tinyint(1)           | YES  |     | NULL    |                |
| visit_total_time          | int(11) unsigned     | NO   |     | NULL    |                |
| location_city             | varchar(255)         | YES  |     | NULL    |                |
| location_country          | char(3)              | YES  |     | NULL    |                |
| location_latitude         | decimal(9,6)         | YES  |     | NULL    |                |
| location_longitude        | decimal(9,6)         | YES  |     | NULL    |                |
| location_region           | char(3)              | YES  |     | NULL    |                |
| custom_var_k1             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v1             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k2             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v2             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k3             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v3             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k4             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v4             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_k5             | varchar(200)         | YES  |     | NULL    |                |
| custom_var_v5             | varchar(200)         | YES  |     | NULL    |                |
+---------------------------+----------------------+------+-----+---------+----------------+
```

### matomo_logger_message
```
+------------------+------------------+------+-----+---------+----------------+
| Field            | Type             | Null | Key | Default | Extra          |
+------------------+------------------+------+-----+---------+----------------+
| idlogger_message | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| tag              | varchar(50)      | YES  |     | NULL    |                |
| timestamp        | timestamp        | YES  |     | NULL    |                |
| level            | varchar(16)      | YES  |     | NULL    |                |
| message          | text             | YES  |     | NULL    |                |
+------------------+------------------+------+-----+---------+----------------+
```

### matomo_option
```
+--------------+--------------+------+-----+---------+-------+
| Field        | Type         | Null | Key | Default | Extra |
+--------------+--------------+------+-----+---------+-------+
| option_name  | varchar(255) | NO   | PRI | NULL    |       |
| option_value | longtext     | NO   |     | NULL    |       |
| autoload     | tinyint(4)   | NO   | MUL | 1       |       |
+--------------+--------------+------+-----+---------+-------+
```

### matomo_plugin_setting
```
+------------------+---------------------+------+-----+---------+----------------+
| Field            | Type                | Null | Key | Default | Extra          |
+------------------+---------------------+------+-----+---------+----------------+
| plugin_name      | varchar(60)         | NO   | MUL | NULL    |                |
| setting_name     | varchar(255)        | NO   |     | NULL    |                |
| setting_value    | longtext            | NO   |     | NULL    |                |
| json_encoded     | tinyint(3) unsigned | NO   |     | 0       |                |
| user_login       | varchar(100)        | NO   |     |         |                |
| idplugin_setting | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
+------------------+---------------------+------+-----+---------+----------------+
```

### matomo_privacy_logdata_anonymizations
```
+---------------------------------+---------------------+------+-----+---------+----------------+
| Field                           | Type                | Null | Key | Default | Extra          |
+---------------------------------+---------------------+------+-----+---------+----------------+
| idlogdata_anonymization         | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
| idsites                         | text                | YES  |     | NULL    |                |
| date_start                      | datetime            | NO   |     | NULL    |                |
| date_end                        | datetime            | NO   |     | NULL    |                |
| anonymize_ip                    | tinyint(1) unsigned | NO   |     | 0       |                |
| anonymize_location              | tinyint(1) unsigned | NO   |     | 0       |                |
| anonymize_userid                | tinyint(1) unsigned | NO   |     | 0       |                |
| unset_visit_columns             | text                | NO   |     | NULL    |                |
| unset_link_visit_action_columns | text                | NO   |     | NULL    |                |
| output                          | mediumtext          | YES  |     | NULL    |                |
| scheduled_date                  | datetime            | YES  |     | NULL    |                |
| job_start_date                  | datetime            | YES  | MUL | NULL    |                |
| job_finish_date                 | datetime            | YES  |     | NULL    |                |
| requester                       | varchar(100)        | NO   |     |         |                |
+---------------------------------+---------------------+------+-----+---------+----------------+
```

### matomo_report
```
+-------------------------------+--------------+------+-----+---------+----------------+
| Field                         | Type         | Null | Key | Default | Extra          |
+-------------------------------+--------------+------+-----+---------+----------------+
| idreport                      | int(11)      | NO   | PRI | NULL    | auto_increment |
| idsite                        | int(11)      | NO   |     | NULL    |                |
| login                         | varchar(100) | NO   |     | NULL    |                |
| description                   | varchar(255) | NO   |     | NULL    |                |
| idsegment                     | int(11)      | YES  |     | NULL    |                |
| period                        | varchar(10)  | NO   |     | NULL    |                |
| hour                          | tinyint(4)   | NO   |     | 0       |                |
| type                          | varchar(10)  | NO   |     | NULL    |                |
| format                        | varchar(10)  | NO   |     | NULL    |                |
| reports                       | text         | NO   |     | NULL    |                |
| parameters                    | text         | YES  |     | NULL    |                |
| ts_created                    | timestamp    | YES  |     | NULL    |                |
| ts_last_sent                  | timestamp    | YES  |     | NULL    |                |
| deleted                       | tinyint(4)   | NO   |     | 0       |                |
| evolution_graph_within_period | tinyint(4)   | NO   |     | 0       |                |
| evolution_graph_period_n      | int(11)      | NO   |     | NULL    |                |
| period_param                  | varchar(10)  | YES  |     | NULL    |                |
+-------------------------------+--------------+------+-----+---------+----------------+
```

### matomo_report_subscriptions
```
+-----------------+--------------+------+-----+-------------------+-------+
| Field           | Type         | Null | Key | Default           | Extra |
+-----------------+--------------+------+-----+-------------------+-------+
| idreport        | int(11)      | NO   | PRI | NULL              |       |
| token           | varchar(100) | YES  | UNI | NULL              |       |
| email           | varchar(100) | NO   | PRI | NULL              |       |
| ts_subscribed   | timestamp    | NO   |     | CURRENT_TIMESTAMP |       |
| ts_unsubscribed | timestamp    | YES  |     | NULL              |       |
+-----------------+--------------+------+-----+-------------------+-------+
```

### matomo_segment
```
+--------------------+--------------+------+-----+---------+----------------+
| Field              | Type         | Null | Key | Default | Extra          |
+--------------------+--------------+------+-----+---------+----------------+
| idsegment          | int(11)      | NO   | PRI | NULL    | auto_increment |
| name               | varchar(255) | NO   |     | NULL    |                |
| definition         | text         | NO   |     | NULL    |                |
| login              | varchar(100) | NO   |     | NULL    |                |
| enable_all_users   | tinyint(4)   | NO   |     | 0       |                |
| enable_only_idsite | int(11)      | YES  |     | NULL    |                |
| auto_archive       | tinyint(4)   | NO   |     | 0       |                |
| ts_created         | timestamp    | YES  |     | NULL    |                |
| ts_last_edit       | timestamp    | YES  |     | NULL    |                |
| deleted            | tinyint(4)   | NO   |     | 0       |                |
+--------------------+--------------+------+-----+---------+----------------+
```

### matomo_sequence
```
+-------+---------------------+------+-----+---------+-------+
| Field | Type                | Null | Key | Default | Extra |
+-------+---------------------+------+-----+---------+-------+
| name  | varchar(120)        | NO   | PRI | NULL    |       |
| value | bigint(20) unsigned | NO   |     | NULL    |       |
+-------+---------------------+------+-----+---------+-------+
```

### matomo_session
```
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| id       | varchar(255) | NO   | PRI | NULL    |       |
| modified | int(11)      | YES  |     | NULL    |       |
| lifetime | int(11)      | YES  |     | NULL    |       |
| data     | text         | YES  |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
```

### matomo_site
```
+--------------------------------+------------------+------+-----+---------+----------------+
| Field                          | Type             | Null | Key | Default | Extra          |
+--------------------------------+------------------+------+-----+---------+----------------+
| idsite                         | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| name                           | varchar(90)      | NO   |     | NULL    |                |
| main_url                       | varchar(255)     | NO   |     | NULL    |                |
| ts_created                     | timestamp        | YES  |     | NULL    |                |
| ecommerce                      | tinyint(4)       | YES  |     | 0       |                |
| sitesearch                     | tinyint(4)       | YES  |     | 1       |                |
| sitesearch_keyword_parameters  | text             | NO   |     | NULL    |                |
| sitesearch_category_parameters | text             | NO   |     | NULL    |                |
| timezone                       | varchar(50)      | NO   |     | NULL    |                |
| currency                       | char(3)          | NO   |     | NULL    |                |
| exclude_unknown_urls           | tinyint(1)       | YES  |     | 0       |                |
| excluded_ips                   | text             | NO   |     | NULL    |                |
| excluded_parameters            | text             | NO   |     | NULL    |                |
| excluded_user_agents           | text             | NO   |     | NULL    |                |
| group                          | varchar(250)     | NO   |     | NULL    |                |
| type                           | varchar(255)     | NO   |     | NULL    |                |
| keep_url_fragment              | tinyint(4)       | NO   |     | 0       |                |
| creator_login                  | varchar(100)     | YES  |     | NULL    |                |
+--------------------------------+------------------+------+-----+---------+----------------+
```

### matomo_site_setting
```
+----------------+---------------------+------+-----+---------+----------------+
| Field          | Type                | Null | Key | Default | Extra          |
+----------------+---------------------+------+-----+---------+----------------+
| idsite         | int(10) unsigned    | NO   | MUL | NULL    |                |
| plugin_name    | varchar(60)         | NO   |     | NULL    |                |
| setting_name   | varchar(255)        | NO   |     | NULL    |                |
| setting_value  | longtext            | NO   |     | NULL    |                |
| json_encoded   | tinyint(3) unsigned | NO   |     | 0       |                |
| idsite_setting | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
+----------------+---------------------+------+-----+---------+----------------+
```

### matomo_site_url
```
+--------+------------------+------+-----+---------+-------+
| Field  | Type             | Null | Key | Default | Extra |
+--------+------------------+------+-----+---------+-------+
| idsite | int(10) unsigned | NO   | PRI | NULL    |       |
| url    | varchar(255)     | NO   | PRI | NULL    |       |
+--------+------------------+------+-----+---------+-------+
```

### matomo_tagmanager_container
```
+--------------+------------------+------+-----+---------+-------+
| Field        | Type             | Null | Key | Default | Extra |
+--------------+------------------+------+-----+---------+-------+
| idcontainer  | varchar(8)       | NO   | PRI | NULL    |       |
| idsite       | int(11) unsigned | NO   | MUL | NULL    |       |
| context      | varchar(10)      | NO   |     | NULL    |       |
| name         | varchar(50)      | NO   |     | NULL    |       |
| description  | varchar(1000)    | NO   |     |         |       |
| status       | varchar(10)      | NO   |     | NULL    |       |
| created_date | datetime         | NO   |     | NULL    |       |
| updated_date | datetime         | NO   |     | NULL    |       |
| deleted_date | datetime         | YES  |     | NULL    |       |
+--------------+------------------+------+-----+---------+-------+
```

### matomo_tagmanager_container_release
```
+--------------------+---------------------+------+-----+---------+----------------+
| Field              | Type                | Null | Key | Default | Extra          |
+--------------------+---------------------+------+-----+---------+----------------+
| idcontainerrelease | bigint(20)          | NO   | PRI | NULL    | auto_increment |
| idcontainer        | varchar(8)          | NO   |     | NULL    |                |
| idcontainerversion | bigint(20) unsigned | NO   |     | NULL    |                |
| idsite             | int(11) unsigned    | NO   | MUL | NULL    |                |
| status             | varchar(10)         | NO   |     | NULL    |                |
| environment        | varchar(40)         | NO   |     | NULL    |                |
| release_login      | varchar(100)        | NO   |     | NULL    |                |
| release_date       | datetime            | NO   |     | NULL    |                |
| deleted_date       | datetime            | YES  |     | NULL    |                |
+--------------------+---------------------+------+-----+---------+----------------+
```

### matomo_tagmanager_container_version
```
+--------------------+-----------------------+------+-----+---------+----------------+
| Field              | Type                  | Null | Key | Default | Extra          |
+--------------------+-----------------------+------+-----+---------+----------------+
| idcontainerversion | bigint(20) unsigned   | NO   | PRI | NULL    | auto_increment |
| idcontainer        | varchar(8)            | NO   | MUL | NULL    |                |
| idsite             | int(11) unsigned      | NO   | MUL | NULL    |                |
| status             | varchar(10)           | NO   |     | NULL    |                |
| revision           | mediumint(8) unsigned | NO   |     | 1       |                |
| name               | varchar(50)           | NO   |     |         |                |
| description        | varchar(1000)         | NO   |     |         |                |
| created_date       | datetime              | NO   |     | NULL    |                |
| updated_date       | datetime              | NO   |     | NULL    |                |
| deleted_date       | datetime              | YES  |     | NULL    |                |
+--------------------+-----------------------+------+-----+---------+----------------+
```

### matomo_tagmanager_tag
```
+--------------------+-----------------------+------+-----+-----------+----------------+
| Field              | Type                  | Null | Key | Default   | Extra          |
+--------------------+-----------------------+------+-----+-----------+----------------+
| idtag              | bigint(20) unsigned   | NO   | PRI | NULL      | auto_increment |
| idcontainerversion | bigint(20) unsigned   | NO   |     | NULL      |                |
| idsite             | int(11) unsigned      | NO   | MUL | NULL      |                |
| type               | varchar(50)           | NO   |     | NULL      |                |
| name               | varchar(50)           | NO   |     | NULL      |                |
| status             | varchar(10)           | NO   |     | NULL      |                |
| parameters         | mediumtext            | NO   |     | NULL      |                |
| fire_trigger_ids   | text                  | NO   |     | NULL      |                |
| block_trigger_ids  | text                  | NO   |     | NULL      |                |
| fire_limit         | varchar(20)           | NO   |     | unlimited |                |
| priority           | smallint(5) unsigned  | NO   |     | NULL      |                |
| fire_delay         | mediumint(8) unsigned | NO   |     | 0         |                |
| start_date         | datetime              | YES  |     | NULL      |                |
| end_date           | datetime              | YES  |     | NULL      |                |
| created_date       | datetime              | NO   |     | NULL      |                |
| updated_date       | datetime              | NO   |     | NULL      |                |
| deleted_date       | datetime              | YES  |     | NULL      |                |
+--------------------+-----------------------+------+-----+-----------+----------------+
```

### matomo_tagmanager_trigger
```
+--------------------+---------------------+------+-----+---------+----------------+
| Field              | Type                | Null | Key | Default | Extra          |
+--------------------+---------------------+------+-----+---------+----------------+
| idtrigger          | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
| idcontainerversion | bigint(20) unsigned | NO   |     | NULL    |                |
| idsite             | int(11) unsigned    | NO   | MUL | NULL    |                |
| type               | varchar(50)         | NO   |     | NULL    |                |
| name               | varchar(50)         | NO   |     | NULL    |                |
| status             | varchar(10)         | NO   |     | NULL    |                |
| parameters         | mediumtext          | NO   |     | NULL    |                |
| conditions         | mediumtext          | NO   |     | NULL    |                |
| created_date       | datetime            | NO   |     | NULL    |                |
| updated_date       | datetime            | NO   |     | NULL    |                |
| deleted_date       | datetime            | YES  |     | NULL    |                |
+--------------------+---------------------+------+-----+---------+----------------+
```

### matomo_tagmanager_variable
```
+--------------------+---------------------+------+-----+---------+----------------+
| Field              | Type                | Null | Key | Default | Extra          |
+--------------------+---------------------+------+-----+---------+----------------+
| idvariable         | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
| idcontainerversion | bigint(20) unsigned | NO   |     | NULL    |                |
| idsite             | int(11) unsigned    | NO   | MUL | NULL    |                |
| type               | varchar(50)         | NO   |     | NULL    |                |
| name               | varchar(50)         | NO   |     | NULL    |                |
| status             | varchar(10)         | NO   |     | NULL    |                |
| parameters         | mediumtext          | NO   |     | NULL    |                |
| lookup_table       | mediumtext          | NO   |     | NULL    |                |
| default_value      | text                | YES  |     | NULL    |                |
| created_date       | datetime            | NO   |     | NULL    |                |
| updated_date       | datetime            | NO   |     | NULL    |                |
| deleted_date       | datetime            | YES  |     | NULL    |                |
+--------------------+---------------------+------+-----+---------+----------------+
```

### matomo_tracking_failure
```
+---------------------+----------------------+------+-----+---------+-------+
| Field               | Type                 | Null | Key | Default | Extra |
+---------------------+----------------------+------+-----+---------+-------+
| idsite              | bigint(20) unsigned  | NO   | PRI | NULL    |       |
| idfailure           | smallint(5) unsigned | NO   | PRI | NULL    |       |
| date_first_occurred | datetime             | NO   |     | NULL    |       |
| request_url         | mediumtext           | NO   |     | NULL    |       |
+---------------------+----------------------+------+-----+---------+-------+
```

### matomo_twofactor_recovery_code
```
+----------------+---------------------+------+-----+---------+----------------+
| Field          | Type                | Null | Key | Default | Extra          |
+----------------+---------------------+------+-----+---------+----------------+
| idrecoverycode | bigint(20) unsigned | NO   | PRI | NULL    | auto_increment |
| login          | varchar(100)        | NO   |     | NULL    |                |
| recovery_code  | varchar(40)         | NO   |     | NULL    |                |
+----------------+---------------------+------+-----+---------+----------------+
```

### matomo_user
```
+----------------------+---------------------+------+-----+---------+-------+
| Field                | Type                | Null | Key | Default | Extra |
+----------------------+---------------------+------+-----+---------+-------+
| login                | varchar(100)        | NO   | PRI | NULL    |       |
| password             | varchar(255)        | NO   |     | NULL    |       |
| alias                | varchar(45)         | NO   |     | NULL    |       |
| email                | varchar(100)        | NO   |     | NULL    |       |
| twofactor_secret     | varchar(40)         | NO   |     |         |       |
| token_auth           | char(32)            | NO   | UNI | NULL    |       |
| superuser_access     | tinyint(2) unsigned | NO   |     | 0       |       |
| date_registered      | timestamp           | YES  |     | NULL    |       |
| ts_password_modified | timestamp           | YES  |     | NULL    |       |
+----------------------+---------------------+------+-----+---------+-------+
```

### matomo_user_dashboard
```
+-------------+--------------+------+-----+---------+-------+
| Field       | Type         | Null | Key | Default | Extra |
+-------------+--------------+------+-----+---------+-------+
| login       | varchar(100) | NO   | PRI | NULL    |       |
| iddashboard | int(11)      | NO   | PRI | NULL    |       |
| name        | varchar(100) | YES  |     | NULL    |       |
| layout      | text         | NO   |     | NULL    |       |
+-------------+--------------+------+-----+---------+-------+
```

### matomo_user_language
```
+-------------------+--------------+------+-----+---------+-------+
| Field             | Type         | Null | Key | Default | Extra |
+-------------------+--------------+------+-----+---------+-------+
| login             | varchar(100) | NO   | PRI | NULL    |       |
| language          | varchar(10)  | NO   |     | NULL    |       |
| use_12_hour_clock | tinyint(1)   | NO   |     | 0       |       |
+-------------------+--------------+------+-----+---------+-------+
```
