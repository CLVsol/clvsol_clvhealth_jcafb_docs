.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

===========================================
*External Sync Batch Log* [*Default Batch*]
===========================================

.. _External Sync Batch - Default Batch - 20190529a:

*External Sync Batch* - *Default Batch* 01 (Execution time: 12:03:30.850)
-------------------------------------------------------------------------

    ::

        ########## Default Batch ##########

        ########## res.country (res.country) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 253
        reg_count: 253
        include_count: 253
        update_count: 0
        task_count: 253

        date_last_sync: 2019-05-29 22:39:11
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:01.696

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 253
        reg_count: 253
        include_count: 223
        task_count: 253

        date_last_sync: 2019-05-29 22:39:12
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:04.201

        ########## res.country.state (res.country.state) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 645
        reg_count: 645
        include_count: 645
        update_count: 0
        task_count: 645

        date_last_sync: 2019-05-29 22:39:17
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:06.260

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 645
        reg_count: 645
        include_count: 640
        task_count: 645

        date_last_sync: 2019-05-29 22:39:23
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:12.412

        ########## res.city (l10n_br_base.city) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 5564
        reg_count: 5564
        include_count: 5564
        update_count: 0
        task_count: 5564

        date_last_sync: 2019-05-29 22:39:35
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:31.832

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 5564
        reg_count: 5564
        include_count: 5564
        task_count: 5564

        date_last_sync: 2019-05-29 22:40:07
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:02:02.018

        ########## clv.global_tag (clv.global_tag) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 26
        reg_count: 26
        include_count: 26
        update_count: 0
        task_count: 26

        date_last_sync: 2019-05-29 22:42:09
        upmost_last_update: 2019-01-21 11:01:59

        Execution time: 0:00:00.364

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 26
        reg_count: 26
        include_count: 26
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 26

        date_last_sync: 2019-05-29 22:42:09
        upmost_last_update: 2019-01-21 11:01:59

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.023

        ########## clv.phase (clv.history_marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 5
        reg_count: 5
        include_count: 5
        update_count: 0
        task_count: 5

        date_last_sync: 2019-05-29 22:42:10
        upmost_last_update: 2018-11-14 14:35:16

        Execution time: 0:00:00.229

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 5
        reg_count: 5
        include_count: 5
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 5

        date_last_sync: 2019-05-29 22:42:11
        upmost_last_update: 2018-11-14 14:35:16

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.351

        ########## hr.department (hr.department) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 52
        reg_count: 52
        include_count: 52
        update_count: 0
        task_count: 52

        date_last_sync: 2019-05-29 22:42:11
        upmost_last_update: 2018-12-05 13:28:15

        Execution time: 0:00:00.533

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 52
        reg_count: 52
        include_count: 52
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 52

        date_last_sync: 2019-05-29 22:42:12
        upmost_last_update: 2018-12-05 13:28:15

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.953

        ########## hr.job (hr.job) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 16
        reg_count: 16
        include_count: 16
        update_count: 0
        task_count: 16

        date_last_sync: 2019-05-29 22:42:14
        upmost_last_update: 2018-12-07 18:19:28

        Execution time: 0:00:00.323

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 16
        reg_count: 16
        include_count: 16
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 16

        date_last_sync: 2019-05-29 22:42:14
        upmost_last_update: 2018-12-07 18:19:28

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.814

        ########## hr.employee (hr.employee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 191
        reg_count: 191
        include_count: 191
        update_count: 0
        task_count: 191

        date_last_sync: 2019-05-29 22:42:15
        upmost_last_update: 2019-01-07 19:29:07

        Execution time: 0:00:01.369

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 191
        reg_count: 191
        include_count: 191
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 191

        date_last_sync: 2019-05-29 22:42:16
        upmost_last_update: 2019-01-07 19:29:07

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:15.451

        ########## survey.stage (survey.stage) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 4
        reg_count: 4
        include_count: 4
        update_count: 0
        task_count: 4

        date_last_sync: 2019-05-29 22:42:32
        upmost_last_update: 2017-10-13 16:31:05

        Execution time: 0:00:00.226

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 4
        reg_count: 4
        include_count: 4
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 4

        date_last_sync: 2019-05-29 22:42:32
        upmost_last_update: 2017-10-13 16:31:05

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.274

        ########## survey.survey (survey.survey) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 36
        reg_count: 36
        include_count: 36
        update_count: 0
        task_count: 36

        date_last_sync: 2019-05-29 22:42:32
        upmost_last_update: 2018-12-07 23:55:16

        Execution time: 0:00:00.429

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 36
        reg_count: 36
        include_count: 36
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 36

        date_last_sync: 2019-05-29 22:42:33
        upmost_last_update: 2018-12-07 23:55:16

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.569

        ########## survey.page (survey.page) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 187
        reg_count: 187
        include_count: 187
        update_count: 0
        task_count: 187

        date_last_sync: 2019-05-29 22:42:34
        upmost_last_update: 2018-12-07 23:55:16

        Execution time: 0:00:01.315

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 187
        reg_count: 187
        include_count: 187
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 187

        date_last_sync: 2019-05-29 22:42:35
        upmost_last_update: 2018-12-07 23:55:16

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:04.547

        ########## survey.question (survey.question) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 816
        reg_count: 816
        include_count: 816
        update_count: 0
        task_count: 816

        date_last_sync: 2019-05-29 22:42:40
        upmost_last_update: 2018-12-07 23:55:16

        Execution time: 0:00:05.204

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 816
        reg_count: 816
        include_count: 816
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 816

        date_last_sync: 2019-05-29 22:42:45
        upmost_last_update: 2018-12-07 23:55:16

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:24.125

        ########## survey.label (survey.label) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 2734
        reg_count: 2734
        include_count: 2734
        update_count: 0
        task_count: 2734

        date_last_sync: 2019-05-29 22:43:09
        upmost_last_update: 2018-12-03 11:39:29

        Execution time: 0:00:16.706

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2734
        reg_count: 2734
        include_count: 2734
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 2734

        date_last_sync: 2019-05-29 22:43:26
        upmost_last_update: 2018-12-03 11:39:29

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:01:05.985

        ########## survey.user_input (survey.user_input) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 3061
        reg_count: 3061
        include_count: 3061
        update_count: 0
        task_count: 3061

        date_last_sync: 2019-05-29 22:44:32
        upmost_last_update: 2019-01-26 11:21:06

        Execution time: 0:00:20.396

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3061
        reg_count: 3061
        include_count: 3061
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3061

        date_last_sync: 2019-05-29 22:44:52
        upmost_last_update: 2019-01-26 11:21:06

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:01:33.099

        ########## survey.user_input_line (survey.user_input_line) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 115369
        reg_count: 115369
        include_count: 115369
        update_count: 0
        task_count: 115369

        date_last_sync: 2019-05-29 22:46:26
        upmost_last_update: 2019-01-26 11:21:06

        Execution time: 0:33:17.177

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 115369
        reg_count: 115369
        include_count: 115369
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 115369

        date_last_sync: 2019-05-29 23:19:43
        upmost_last_update: 2019-01-26 11:21:06

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 2:53:42.220

        ########## clv.event (clv.event) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 24
        reg_count: 24
        include_count: 24
        update_count: 0
        task_count: 24

        date_last_sync: 2019-05-30 02:13:25
        upmost_last_update: 2019-04-10 14:59:18

        Execution time: 0:00:00.748

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 24
        reg_count: 24
        include_count: 24
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 24

        date_last_sync: 2019-05-30 02:13:26
        upmost_last_update: 2019-04-10 14:59:18

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.311

        ########## clv.event.attendee (clv.event.attendee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: []

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 1081
        reg_count: 1081
        include_count: 1081
        update_count: 0
        task_count: 1081

        date_last_sync: 2019-05-30 02:13:27
        upmost_last_update: 2019-01-25 16:14:21

        Execution time: 0:00:24.346

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1081
        reg_count: 1081
        include_count: 1081
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1081

        date_last_sync: 2019-05-30 02:13:51
        upmost_last_update: 2019-01-25 16:14:21

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:59.833

        ########## clv.document.category (clv.document.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 4
        reg_count: 4
        include_count: 4
        update_count: 0
        task_count: 4

        date_last_sync: 2019-05-30 02:14:51
        upmost_last_update: 2018-01-20 19:29:29

        Execution time: 0:00:00.298

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 4
        reg_count: 4
        include_count: 4
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 4

        date_last_sync: 2019-05-30 02:14:52
        upmost_last_update: 2018-01-20 19:29:29

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.327

        ########## clv.document.type (clv.document.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 33
        reg_count: 33
        include_count: 33
        update_count: 0
        task_count: 33

        date_last_sync: 2019-05-30 02:14:52
        upmost_last_update: 2019-01-15 19:42:39

        Execution time: 0:00:00.944

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 33
        reg_count: 33
        include_count: 33
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 33

        date_last_sync: 2019-05-30 02:14:53
        upmost_last_update: 2019-01-15 19:42:39

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.919

        ########## clv.document (clv.document) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 5451
        reg_count: 5451
        include_count: 5451
        update_count: 0
        task_count: 5451

        date_last_sync: 2019-05-30 02:14:54
        upmost_last_update: 2019-03-24 01:59:00

        Execution time: 0:02:05.328

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 5451
        reg_count: 5451
        include_count: 5451
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 5451

        date_last_sync: 2019-05-30 02:16:59
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: clv.document.code
        sequence_number_next_actual: 6686

        Execution time: 0:13:39.688

        ########## clv.document.item (clv.document.item) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 166230
        reg_count: 166230
        include_count: 166230
        update_count: 0
        task_count: 166230

        date_last_sync: 2019-05-30 02:30:39
        upmost_last_update: 2019-03-23 20:08:51

        Execution time: 1:40:21.944

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 166230
        reg_count: 166230
        include_count: 166230
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 166230

        date_last_sync: 2019-05-30 04:11:01
        upmost_last_update: 2019-03-23 20:08:51

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 2:47:56.553

        ########## clv.mfile (clv.mfile) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 3719
        reg_count: 3719
        include_count: 3719
        update_count: 0
        task_count: 3719

        date_last_sync: 2019-05-30 06:58:57
        upmost_last_update: 2019-03-24 01:59:00

        Execution time: 0:02:43.591

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3719
        reg_count: 3719
        include_count: 3719
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3719

        date_last_sync: 2019-05-30 07:01:41
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:06:26.718

        ########## clv.lab_test.unit (clv.lab_test.unit) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 9
        reg_count: 9
        include_count: 9
        update_count: 0
        task_count: 9

        date_last_sync: 2019-05-30 07:08:08
        upmost_last_update: 2019-01-16 15:25:52

        Execution time: 0:00:00.616

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 9
        reg_count: 9
        include_count: 9
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 9

        date_last_sync: 2019-05-30 07:08:08
        upmost_last_update: 2019-01-16 15:25:52

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.428

        ########## clv.lab_test.type (clv.lab_test.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 15
        reg_count: 15
        include_count: 15
        update_count: 0
        task_count: 15

        date_last_sync: 2019-05-30 07:08:09
        upmost_last_update: 2019-01-19 17:46:08

        Execution time: 0:00:00.881

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 15
        reg_count: 15
        include_count: 15
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 15

        date_last_sync: 2019-05-30 07:08:10
        upmost_last_update: 2019-01-19 17:46:08

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.136

        ########## clv.lab_test.request (clv.lab_test.request) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 3179
        reg_count: 3179
        include_count: 3179
        update_count: 0
        task_count: 3179

        date_last_sync: 2019-05-30 07:08:11
        upmost_last_update: 2019-03-24 01:59:00

        Execution time: 0:02:21.821

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3179
        reg_count: 3179
        include_count: 3179
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3179

        date_last_sync: 2019-05-30 07:10:33
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: clv.lab_test.request.code
        sequence_number_next_actual: 3848

        Execution time: 0:07:44.187

        ########## clv.lab_test.result (clv.lab_test.result) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 2191
        reg_count: 2191
        include_count: 2191
        update_count: 0
        task_count: 2191

        date_last_sync: 2019-05-30 07:18:17
        upmost_last_update: 2019-03-24 01:59:00

        Execution time: 0:01:39.547

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2191
        reg_count: 2191
        include_count: 2191
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 2191

        date_last_sync: 2019-05-30 07:19:56
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: clv.lab_test.result.code
        sequence_number_next_actual: 2519

        Execution time: 0:07:10.136

        ########## clv.lab_test.report (clv.lab_test.report) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 1452
        reg_count: 1452
        include_count: 1452
        update_count: 0
        task_count: 1452

        date_last_sync: 2019-05-30 07:27:07
        upmost_last_update: 2019-01-25 20:57:19

        Execution time: 0:01:05.721

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1452
        reg_count: 1452
        include_count: 1452
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1452

        date_last_sync: 2019-05-30 07:28:12
        upmost_last_update: 2019-01-25 20:57:19

        sequence_code: clv.lab_test.report.code
        sequence_number_next_actual: 1846

        Execution time: 0:04:03.715

        ########## clv.lab_test.criterion (clv.lab_test.criterion) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 72773
        reg_count: 72773
        include_count: 72773
        update_count: 0
        task_count: 72773

        date_last_sync: 2019-05-30 07:32:16
        upmost_last_update: 2019-01-25 20:57:19

        Execution time: 1:02:04.180

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 72773
        reg_count: 72773
        include_count: 72773
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 72773

        date_last_sync: 2019-05-30 08:34:20
        upmost_last_update: 2019-01-25 20:57:19

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 1:38:15.874

        ########## clv.address.category (clv.address.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 2
        reg_count: 2
        include_count: 2
        update_count: 0
        task_count: 2

        date_last_sync: 2019-05-30 10:12:36
        upmost_last_update: 2019-01-25 17:27:25

        Execution time: 0:00:00.350

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2
        reg_count: 2
        include_count: 2
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 2

        date_last_sync: 2019-05-30 10:12:37
        upmost_last_update: 2019-01-25 17:27:25

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.385

        ########## clv.address (clv.address) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 575
        reg_count: 575
        include_count: 575
        update_count: 0
        task_count: 575

        date_last_sync: 2019-05-30 10:12:37
        upmost_last_update: 2019-03-24 13:31:15

        Execution time: 0:00:31.159

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 575
        reg_count: 575
        include_count: 575
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 575

        date_last_sync: 2019-05-30 10:13:08
        upmost_last_update: 2019-03-24 13:31:15

        sequence_code: clv.address.code
        sequence_number_next_actual: 611

        Execution time: 0:03:29.076

        ########## clv.address.history (clv.address.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 1225
        reg_count: 1225
        include_count: 1225
        update_count: 0
        task_count: 1225

        date_last_sync: 2019-05-30 10:16:37
        upmost_last_update: 2019-03-24 13:32:50

        Execution time: 0:01:06.966

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1225
        reg_count: 1225
        include_count: 1225
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1225

        date_last_sync: 2019-05-30 10:17:44
        upmost_last_update: 2019-03-24 13:32:50

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:03:43.560

        ########## clv.person.category (clv.person.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 2
        reg_count: 2
        include_count: 2
        update_count: 0
        task_count: 2

        date_last_sync: 2019-05-30 10:21:28
        upmost_last_update: 2017-10-18 23:24:40

        Execution time: 0:00:00.318

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2
        reg_count: 2
        include_count: 2
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 2

        date_last_sync: 2019-05-30 10:21:28
        upmost_last_update: 2017-10-18 23:24:40

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.333

        ########## clv.person.marker (clv.person.marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 3
        reg_count: 3
        include_count: 3
        update_count: 0
        task_count: 3

        date_last_sync: 2019-05-30 10:21:28
        upmost_last_update: 2018-11-27 18:26:38

        Execution time: 0:00:00.375

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3
        reg_count: 3
        include_count: 3
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3

        date_last_sync: 2019-05-30 10:21:29
        upmost_last_update: 2018-11-27 18:26:38

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.332

        ########## clv.person (clv.person) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 1375
        reg_count: 1375
        include_count: 1375
        update_count: 0
        task_count: 1375

        date_last_sync: 2019-05-30 10:21:29
        upmost_last_update: 2019-04-22 14:46:12

        Execution time: 0:01:15.532

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1375
        reg_count: 1375
        include_count: 1375
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1375

        date_last_sync: 2019-05-30 10:22:45
        upmost_last_update: 2019-04-22 14:46:12

        sequence_code: clv.person.code
        sequence_number_next_actual: 1537

        Execution time: 0:07:05.112

        ########## clv.person.history (clv.person.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: False
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_identify"...

        external_args: ['|', ('active', '=', True), ('active', '=', False)]

        external_object_ids: 0
        sync_objects: 0
        reg_count_2: 0
        missing_count: 0

        external_objects: 3150
        reg_count: 3150
        include_count: 3150
        update_count: 0
        task_count: 3150

        date_last_sync: 2019-05-30 10:29:50
        upmost_last_update: 2019-03-24 13:41:14

        Execution time: 0:02:52.438

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3150
        reg_count: 3150
        include_count: 3150
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3150

        date_last_sync: 2019-05-30 10:32:42
        upmost_last_update: 2019-03-24 13:41:14

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:09:59.192

        ############################################################
        Execution time: 12:03:30.850

.. _External Sync Batch - Default Batch - 20190530a:

*External Sync Batch* - *Default Batch* 02 (Execution time: 0:55:22.890)
------------------------------------------------------------------------

    ::

        ########## Default Batch ##########

        ########## res.country (res.country) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 30
        reg_count: 30
        include_count: 0
        task_count: 30

        date_last_sync: 2019-05-30 13:30:02
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:00.687

        ########## res.country.state (res.country.state) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 5
        reg_count: 5
        include_count: 0
        task_count: 5

        date_last_sync: 2019-05-30 13:30:02
        upmost_last_update: 2017-10-13 16:30:19

        Execution time: 0:00:00.618

        ########## res.city (l10n_br_base.city) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        task_count: 0

        date_last_sync: 2019-05-30 13:30:03
        upmost_last_update: False

        Execution time: 0:00:00.288

        ########## clv.global_tag (clv.global_tag) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:03
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.280

        ########## clv.phase (clv.history_marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:04
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.262

        ########## hr.department (hr.department) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:04
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.270

        ########## hr.job (hr.job) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:04
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.270

        ########## hr.employee (hr.employee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:04
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.300

        ########## survey.stage (survey.stage) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:05
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.313

        ########## survey.survey (survey.survey) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:05
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.277

        ########## survey.page (survey.page) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:05
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.268

        ########## survey.question (survey.question) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:06
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.275

        ########## survey.label (survey.label) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:06
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.267

        ########## survey.user_input (survey.user_input) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:06
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.293

        ########## survey.user_input_line (survey.user_input_line) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:07
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.280

        ########## clv.event (clv.event) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:30:07
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.272

        ########## clv.event.attendee (clv.event.attendee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1081
        reg_count: 1081
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 1081
        sync_count: 1081

        task_count: 1081

        date_last_sync: 2019-05-30 13:30:07
        upmost_last_update: 2019-01-25 16:14:21

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:02:05.250

        ########## clv.document.category (clv.document.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:32:12
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.266

        ########## clv.document.type (clv.document.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 13:32:13
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.268

        ########## clv.document (clv.document) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 5448
        reg_count: 5448
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 5448
        sync_count: 5448

        task_count: 5448

        date_last_sync: 2019-05-30 13:32:13
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: clv.document.code
        sequence_number_next_actual: 6686

        Execution time: 0:29:10.253

        ########## clv.document.item (clv.document.item) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:01:23
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.245

        ########## clv.mfile (clv.mfile) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:01:23
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.245

        ########## clv.lab_test.unit (clv.lab_test.unit) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:01:24
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.249

        ########## clv.lab_test.type (clv.lab_test.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:01:24
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.244

        ########## clv.lab_test.request (clv.lab_test.request) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3177
        reg_count: 3177
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 3177
        sync_count: 3177

        task_count: 3177

        date_last_sync: 2019-05-30 14:01:24
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: clv.lab_test.request.code
        sequence_number_next_actual: 3848

        Execution time: 0:09:34.095

        ########## clv.lab_test.result (clv.lab_test.result) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2189
        reg_count: 2189
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 2189
        sync_count: 2189

        task_count: 2189

        date_last_sync: 2019-05-30 14:10:58
        upmost_last_update: 2019-03-24 01:59:00

        sequence_code: clv.lab_test.result.code
        sequence_number_next_actual: 2519

        Execution time: 0:08:48.919

        ########## clv.lab_test.report (clv.lab_test.report) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1452
        reg_count: 1452
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 1452
        sync_count: 1452

        task_count: 1452

        date_last_sync: 2019-05-30 14:19:47
        upmost_last_update: 2019-01-25 20:57:19

        sequence_code: clv.lab_test.report.code
        sequence_number_next_actual: 1846

        Execution time: 0:05:03.890

        ########## clv.lab_test.criterion (clv.lab_test.criterion) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:24:51
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.258

        ########## clv.address.category (clv.address.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:24:51
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.262

        ########## clv.address (clv.address) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:24:52
        upmost_last_update: False

        sequence_code: clv.address.code
        sequence_number_next_actual: 611

        Execution time: 0:00:00.267

        ########## clv.address.history (clv.address.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:24:52
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.242

        ########## clv.person.category (clv.person.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:24:52
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.257

        ########## clv.person.marker (clv.person.marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:24:52
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.251

        ########## clv.person (clv.person) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 83
        reg_count: 83
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 83
        sync_count: 83

        task_count: 83

        date_last_sync: 2019-05-30 14:24:53
        upmost_last_update: 2019-03-24 13:31:15

        sequence_code: clv.person.code
        sequence_number_next_actual: 1537

        Execution time: 0:00:31.528

        ########## clv.person.history (clv.person.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.152
        external_dbname: clvhealth_jcafb_2019

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 0

        date_last_sync: 2019-05-30 14:25:24
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.250

        ############################################################
        Execution time: 0:55:22.890
