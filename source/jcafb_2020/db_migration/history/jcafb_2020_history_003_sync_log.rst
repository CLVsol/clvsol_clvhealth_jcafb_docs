.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

===========================================
*External Sync Batch Log* [*Default Batch*]
===========================================

.. _External Sync Batch - Default Batch - 20190706b:

*External Sync Batch* - *Default Batch* 02 (Execution time: 0:00:24.331)
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

        date_last_sync: 2019-07-06 23:43:27
        upmost_last_update: 2017-10-13 16:31:10

        Execution time: 0:00:00.596

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

        date_last_sync: 2019-07-06 23:43:27
        upmost_last_update: 2017-10-13 16:30:19

        Execution time: 0:00:00.269

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

        date_last_sync: 2019-07-06 23:43:28
        upmost_last_update: False

        Execution time: 0:00:00.184

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

        date_last_sync: 2019-07-06 23:43:28
        upmost_last_update: 2019-01-21 11:01:59

        Execution time: 0:00:00.389

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

        date_last_sync: 2019-07-06 23:43:28
        upmost_last_update: 2019-01-21 11:01:59

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.988

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

        date_last_sync: 2019-07-06 23:43:29
        upmost_last_update: 2018-11-14 14:35:16

        Execution time: 0:00:00.240

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

        date_last_sync: 2019-07-06 23:43:30
        upmost_last_update: 2018-11-14 14:35:16

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.298

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

        date_last_sync: 2019-07-06 23:43:30
        upmost_last_update: 2018-12-05 13:28:15

        Execution time: 0:00:00.489

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

        date_last_sync: 2019-07-06 23:43:30
        upmost_last_update: 2018-12-05 13:28:15

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.974

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

        date_last_sync: 2019-07-06 23:43:32
        upmost_last_update: 2018-12-07 18:19:28

        Execution time: 0:00:00.276

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

        date_last_sync: 2019-07-06 23:43:33
        upmost_last_update: 2018-12-07 18:19:28

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.793

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

        enable_sequence_code_sync: True

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

        date_last_sync: 2019-07-06 23:43:33
        upmost_last_update: 2019-01-07 19:29:07

        Execution time: 0:00:01.417

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

        date_last_sync: 2019-07-06 23:43:35
        upmost_last_update: 2019-01-07 19:29:07

        sequence_code: hr.employee.code
        sequence_number_next_actual: 193

        Execution time: 0:00:16.276

        ############################################################
        Execution time: 0:00:24.331
