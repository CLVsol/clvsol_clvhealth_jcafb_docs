.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================
*External Sync Batch Log* [*Default Batch*]
===========================================

.. _External Sync Batch - Default Batch - 20200330:

*External Sync Batch* - *Default Batch* (Execution time: 1:03:48.140)
---------------------------------------------------------------------

    ::

        ########## Default Batch ##########

        ########## res.country (res.country) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 250
        reg_count: 250
        include_count: 250
        update_count: 0
        task_count: 250

        date_last_sync: 2020-03-30 17:34:06
        upmost_last_update: 2019-07-11 20:13:11

        Execution time: 0:00:01.613

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 250
        reg_count: 250
        include_count: 250
        task_count: 250

        date_last_sync: 2020-03-30 17:34:07
        upmost_last_update: 2019-07-11 20:13:11

        Execution time: 0:00:07.029

        ########## res.country.state (res.country.state) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 679
        reg_count: 679
        include_count: 679
        update_count: 0
        task_count: 679

        date_last_sync: 2020-03-30 17:34:14
        upmost_last_update: 2019-07-11 20:13:11

        Execution time: 0:00:03.605

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 679
        reg_count: 679
        include_count: 671
        task_count: 679

        date_last_sync: 2020-03-30 17:34:18
        upmost_last_update: 2019-07-11 20:13:11

        Execution time: 0:00:19.444

        ########## res.city (res.city) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 17:34:37
        upmost_last_update: 2019-07-11 20:13:11

        Execution time: 0:00:32.055

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 5564
        reg_count: 5564
        include_count: 5564
        task_count: 5564

        date_last_sync: 2020-03-30 17:35:09
        upmost_last_update: 2019-07-11 20:13:11

        Execution time: 0:03:04.227

        ########## res.users (res.users) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 190
        reg_count: 190
        include_count: 190
        update_count: 0
        task_count: 190

        date_last_sync: 2020-03-30 17:38:14
        upmost_last_update: 2020-03-02 20:02:10

        Execution time: 0:00:01.570

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 190
        reg_count: 190
        include_count: 190
        task_count: 190

        date_last_sync: 2020-03-30 17:38:15
        upmost_last_update: 2020-03-02 20:02:10

        Execution time: 0:00:08.164

        ########## clv.global_tag (clv.global_tag) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 17:38:23
        upmost_last_update: 2019-07-12 17:43:45

        Execution time: 0:00:00.335

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

        date_last_sync: 2020-03-30 17:38:24
        upmost_last_update: 2019-07-12 17:43:45

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.301

        ########## clv.phase (clv.phase) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 17:38:25
        upmost_last_update: 2019-07-22 18:26:33

        Execution time: 0:00:00.207

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

        date_last_sync: 2020-03-30 17:38:25
        upmost_last_update: 2019-07-22 18:26:33

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.332

        ########## hr.department (hr.department) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 70
        reg_count: 70
        include_count: 70
        update_count: 0
        task_count: 70

        date_last_sync: 2020-03-30 17:38:26
        upmost_last_update: 2020-01-23 17:10:03

        Execution time: 0:00:00.541

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 70
        reg_count: 70
        include_count: 70
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 70

        date_last_sync: 2020-03-30 17:38:26
        upmost_last_update: 2020-01-23 17:10:03

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:03.071

        ########## hr.job (hr.job) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 18
        reg_count: 18
        include_count: 18
        update_count: 0
        task_count: 18

        date_last_sync: 2020-03-30 17:38:29
        upmost_last_update: 2020-01-15 13:33:56

        Execution time: 0:00:00.316

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 18
        reg_count: 18
        include_count: 18
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 18

        date_last_sync: 2020-03-30 17:38:30
        upmost_last_update: 2020-01-15 13:33:56

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.055

        ########## hr.employee (hr.employee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 248
        reg_count: 248
        include_count: 248
        update_count: 0
        task_count: 248

        date_last_sync: 2020-03-30 17:38:31
        upmost_last_update: 2020-01-24 12:20:43

        Execution time: 0:00:01.511

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 248
        reg_count: 248
        include_count: 248
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 248

        date_last_sync: 2020-03-30 17:38:32
        upmost_last_update: 2020-01-24 12:20:43

        sequence_code: hr.employee.code
        sequence_number_next_actual: 250

        Execution time: 0:00:30.093

        ########## hr.employee.history (hr.employee.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 240
        reg_count: 240
        include_count: 240
        update_count: 0
        task_count: 240

        date_last_sync: 2020-03-30 17:39:02
        upmost_last_update: 2019-07-12 17:51:50

        Execution time: 0:00:01.424

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 240
        reg_count: 240
        include_count: 240
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 240

        date_last_sync: 2020-03-30 17:39:04
        upmost_last_update: 2019-07-12 17:51:50

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:11.928

        ########## clv.address.category (clv.address.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 17:39:16
        upmost_last_update: 2019-11-07 18:01:03

        Execution time: 0:00:00.215

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

        date_last_sync: 2020-03-30 17:39:16
        upmost_last_update: 2019-11-07 18:01:03

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.241

        ########## clv.address (clv.address) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 665
        reg_count: 665
        include_count: 665
        update_count: 0
        task_count: 665

        date_last_sync: 2020-03-30 17:39:16
        upmost_last_update: 2020-01-24 19:19:22

        Execution time: 0:00:03.635

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 665
        reg_count: 665
        include_count: 665
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 665

        date_last_sync: 2020-03-30 17:39:20
        upmost_last_update: 2020-01-24 19:19:22

        sequence_code: clv.address.code
        sequence_number_next_actual: 705

        Execution time: 0:01:55.671

        ########## clv.address_aux (clv.address_aux) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 202
        reg_count: 202
        include_count: 202
        update_count: 0
        task_count: 202

        date_last_sync: 2020-03-30 17:41:15
        upmost_last_update: 2020-01-22 17:17:43

        Execution time: 0:00:01.446

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 202
        reg_count: 202
        include_count: 202
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 202

        date_last_sync: 2020-03-30 17:41:17
        upmost_last_update: 2020-01-22 17:17:43

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:32.994

        ########## clv.address.history (clv.address.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 1680
        reg_count: 1680
        include_count: 1680
        update_count: 0
        task_count: 1680

        date_last_sync: 2020-03-30 17:41:50
        upmost_last_update: 2020-03-28 14:30:21

        Execution time: 0:00:09.908

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1680
        reg_count: 1680
        include_count: 1680
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1680

        date_last_sync: 2020-03-30 17:42:00
        upmost_last_update: 2020-03-28 14:30:21

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:01:38.385

        ########## clv.family.category (clv.family.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 0
        reg_count: 0
        include_count: 0
        update_count: 0
        task_count: 0

        date_last_sync: 2020-03-30 17:43:38
        upmost_last_update: False

        Execution time: 0:00:00.233

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

        date_last_sync: 2020-03-30 17:43:38
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.190

        ########## clv.family (clv.family) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 441
        reg_count: 441
        include_count: 441
        update_count: 0
        task_count: 441

        date_last_sync: 2020-03-30 17:43:39
        upmost_last_update: 2020-01-24 19:20:17

        Execution time: 0:00:03.292

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 441
        reg_count: 441
        include_count: 441
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 441

        date_last_sync: 2020-03-30 17:43:42
        upmost_last_update: 2020-01-24 19:20:17

        sequence_code: clv.family.code
        sequence_number_next_actual: 442

        Execution time: 0:01:09.708

        ########## clv.family.history (clv.family.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 743
        reg_count: 743
        include_count: 743
        update_count: 0
        task_count: 743

        date_last_sync: 2020-03-30 17:44:52
        upmost_last_update: 2020-03-28 14:33:17

        Execution time: 0:00:04.618

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 743
        reg_count: 743
        include_count: 743
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 743

        date_last_sync: 2020-03-30 17:44:56
        upmost_last_update: 2020-03-28 14:33:17

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:42.131

        ########## clv.person.category (clv.person.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 17:45:38
        upmost_last_update: 2019-11-05 12:55:52

        Execution time: 0:00:00.212

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

        date_last_sync: 2020-03-30 17:45:39
        upmost_last_update: 2019-11-05 12:55:52

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.280

        ########## clv.person.marker (clv.person.marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 17:45:39
        upmost_last_update: 2019-11-19 19:29:31

        Execution time: 0:00:00.224

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

        date_last_sync: 2020-03-30 17:45:39
        upmost_last_update: 2019-11-19 19:29:31

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.348

        ########## clv.person (clv.person) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 1540
        reg_count: 1540
        include_count: 1540
        update_count: 0
        task_count: 1540

        date_last_sync: 2020-03-30 17:45:39
        upmost_last_update: 2020-01-24 19:30:17

        Execution time: 0:00:09.463

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1540
        reg_count: 1540
        include_count: 1540
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1540

        date_last_sync: 2020-03-30 17:45:49
        upmost_last_update: 2020-01-24 19:30:17

        sequence_code: clv.person.code
        sequence_number_next_actual: 1705

        Execution time: 0:04:48.689

        ########## clv.person.history (clv.person.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 4605
        reg_count: 4605
        include_count: 4605
        update_count: 0
        task_count: 4605

        date_last_sync: 2020-03-30 17:50:38
        upmost_last_update: 2020-03-28 14:23:58

        Execution time: 0:00:34.043

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 4605
        reg_count: 4605
        include_count: 4605
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 4605

        date_last_sync: 2020-03-30 17:51:12
        upmost_last_update: 2020-03-28 14:23:58

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:05:42.187

        ########## clv.person_aux (clv.person_aux) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 605
        reg_count: 605
        include_count: 605
        update_count: 0
        task_count: 605

        date_last_sync: 2020-03-30 17:56:54
        upmost_last_update: 2020-01-24 19:34:55

        Execution time: 0:00:04.961

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 605
        reg_count: 605
        include_count: 605
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 605

        date_last_sync: 2020-03-30 17:56:59
        upmost_last_update: 2020-01-24 19:34:55

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:02:02.107

        ########## survey.stage (survey.stage) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 8
        reg_count: 8
        include_count: 8
        update_count: 0
        task_count: 8

        date_last_sync: 2020-03-30 17:59:01
        upmost_last_update: 2020-01-24 17:37:04

        Execution time: 0:00:00.275

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 8
        reg_count: 8
        include_count: 8
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 8

        date_last_sync: 2020-03-30 17:59:01
        upmost_last_update: 2020-01-24 17:37:04

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.414

        ########## survey.survey (survey.survey) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 54
        reg_count: 54
        include_count: 54
        update_count: 0
        task_count: 54

        date_last_sync: 2020-03-30 17:59:02
        upmost_last_update: 2020-01-17 16:55:10

        Execution time: 0:00:00.638

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 54
        reg_count: 54
        include_count: 54
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 54

        date_last_sync: 2020-03-30 17:59:02
        upmost_last_update: 2020-01-17 16:55:10

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:03.077

        ########## survey.page (survey.page) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 277
        reg_count: 277
        include_count: 277
        update_count: 0
        task_count: 277

        date_last_sync: 2020-03-30 17:59:05
        upmost_last_update: 2020-01-17 16:55:10

        Execution time: 0:00:02.312

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 277
        reg_count: 277
        include_count: 277
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 277

        date_last_sync: 2020-03-30 17:59:08
        upmost_last_update: 2020-01-17 16:55:10

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:10.658

        ########## survey.question (survey.question) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 1209
        reg_count: 1209
        include_count: 1209
        update_count: 0
        task_count: 1209

        date_last_sync: 2020-03-30 17:59:18
        upmost_last_update: 2020-01-17 16:55:10

        Execution time: 0:00:09.419

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1209
        reg_count: 1209
        include_count: 1209
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1209

        date_last_sync: 2020-03-30 17:59:28
        upmost_last_update: 2020-01-17 16:55:10

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:52.787

        ########## survey.label (survey.label) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 3903
        reg_count: 3903
        include_count: 3903
        update_count: 0
        task_count: 3903

        date_last_sync: 2020-03-30 18:00:21
        upmost_last_update: 2020-01-17 16:55:10

        Execution time: 0:00:31.717

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3903
        reg_count: 3903
        include_count: 3903
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3903

        date_last_sync: 2020-03-30 18:00:52
        upmost_last_update: 2020-01-17 16:55:10

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:02:26.816

        ########## survey.user_input (survey.user_input) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 3831
        reg_count: 3831
        include_count: 3831
        update_count: 0
        task_count: 3831

        date_last_sync: 2020-03-30 18:03:19
        upmost_last_update: 2020-01-24 23:11:25

        Execution time: 0:00:33.536

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3831
        reg_count: 3831
        include_count: 3831
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 3831

        date_last_sync: 2020-03-30 18:03:53
        upmost_last_update: 2020-01-24 23:11:25

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:03:39.541

        ########## clv.event (clv.event) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 32
        reg_count: 32
        include_count: 32
        update_count: 0
        task_count: 32

        date_last_sync: 2020-03-30 18:07:32
        upmost_last_update: 2020-01-18 11:30:23

        Execution time: 0:00:00.472

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 32
        reg_count: 32
        include_count: 32
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 32

        date_last_sync: 2020-03-30 18:07:33
        upmost_last_update: 2020-01-18 11:30:23

        sequence_code: clv.event.code
        sequence_number_next_actual: 34

        Execution time: 0:00:01.786

        ########## clv.event.attendee (clv.event.attendee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 1406
        reg_count: 1406
        include_count: 1406
        update_count: 0
        task_count: 1406

        date_last_sync: 2020-03-30 18:07:34
        upmost_last_update: 2020-01-24 19:37:49

        Execution time: 0:00:12.202

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 1406
        reg_count: 1406
        include_count: 1406
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 1406

        date_last_sync: 2020-03-30 18:07:47
        upmost_last_update: 2020-01-24 19:37:49

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:01:02.931

        ########## clv.document.category (clv.document.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 18:08:50
        upmost_last_update: 2020-01-17 17:05:10

        Execution time: 0:00:00.277

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

        date_last_sync: 2020-03-30 18:08:50
        upmost_last_update: 2020-01-17 17:05:10

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.488

        ########## clv.document.type (clv.document.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 44
        reg_count: 44
        include_count: 44
        update_count: 0
        task_count: 44

        date_last_sync: 2020-03-30 18:08:50
        upmost_last_update: 2020-01-18 16:41:29

        Execution time: 0:00:00.573

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 44
        reg_count: 44
        include_count: 44
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 44

        date_last_sync: 2020-03-30 18:08:51
        upmost_last_update: 2020-01-18 16:41:29

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.904

        ########## clv.document (clv.document) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 7438
        reg_count: 7438
        include_count: 7438
        update_count: 0
        task_count: 7438

        date_last_sync: 2020-03-30 18:08:53
        upmost_last_update: 2020-01-25 14:38:34

        Execution time: 0:01:11.303

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 7438
        reg_count: 7438
        include_count: 7438
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 7438

        date_last_sync: 2020-03-30 18:10:04
        upmost_last_update: 2020-01-25 14:38:34

        sequence_code: clv.document.code
        sequence_number_next_actual: 8674

        Execution time: 0:13:26.957

        ########## clv.lab_test.unit (clv.lab_test.unit) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 10
        reg_count: 10
        include_count: 10
        update_count: 0
        task_count: 10

        date_last_sync: 2020-03-30 18:23:31
        upmost_last_update: 2019-11-29 15:52:18

        Execution time: 0:00:00.338

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 10
        reg_count: 10
        include_count: 10
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 10

        date_last_sync: 2020-03-30 18:23:32
        upmost_last_update: 2019-11-29 15:52:18

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.478

        ########## clv.lab_test.parasite (clv.lab_test.parasite) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 16
        reg_count: 16
        include_count: 16
        update_count: 0
        task_count: 16

        date_last_sync: 2020-03-30 18:23:32
        upmost_last_update: 2020-01-16 17:51:12

        Execution time: 0:00:00.379

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 16
        reg_count: 16
        include_count: 16
        task_count: 16

        date_last_sync: 2020-03-30 18:23:32
        upmost_last_update: 2020-01-16 17:51:12

        Execution time: 0:00:00.646

        ########## clv.lab_test.crystal (clv.lab_test.crystal) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 12
        reg_count: 12
        include_count: 12
        update_count: 0
        task_count: 12

        date_last_sync: 2020-03-30 18:23:33
        upmost_last_update: 2020-01-15 22:17:16

        Execution time: 0:00:00.414

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 12
        reg_count: 12
        include_count: 12
        task_count: 12

        date_last_sync: 2020-03-30 18:23:33
        upmost_last_update: 2020-01-15 22:17:16

        Execution time: 0:00:00.680

        ########## clv.lab_test.type (clv.lab_test.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 21
        reg_count: 21
        include_count: 21
        update_count: 0
        task_count: 21

        date_last_sync: 2020-03-30 18:23:34
        upmost_last_update: 2019-12-23 19:06:45

        Execution time: 0:00:00.414

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 21
        reg_count: 21
        include_count: 21
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 21

        date_last_sync: 2020-03-30 18:23:35
        upmost_last_update: 2019-12-23 19:06:45

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:01.134

        ########## clv.lab_test.request (clv.lab_test.request) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 4342
        reg_count: 4342
        include_count: 4342
        update_count: 0
        task_count: 4342

        date_last_sync: 2020-03-30 18:23:36
        upmost_last_update: 2020-01-25 13:09:34

        Execution time: 0:00:44.688

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 4342
        reg_count: 4342
        include_count: 4342
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 4342

        date_last_sync: 2020-03-30 18:24:20
        upmost_last_update: 2020-01-25 13:09:34

        sequence_code: clv.lab_test.request.code
        sequence_number_next_actual: 5014

        Execution time: 0:05:13.299

        ########## clv.lab_test.result (clv.lab_test.result) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 2809
        reg_count: 2809
        include_count: 2809
        update_count: 0
        task_count: 2809

        date_last_sync: 2020-03-30 18:29:34
        upmost_last_update: 2020-01-25 13:11:13

        Execution time: 0:00:30.964

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2809
        reg_count: 2809
        include_count: 2809
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 2809

        date_last_sync: 2020-03-30 18:30:05
        upmost_last_update: 2020-01-25 13:11:13

        sequence_code: clv.lab_test.result.code
        sequence_number_next_actual: 3137

        Execution time: 0:04:18.580

        ########## clv.lab_test.report (clv.lab_test.report) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 2070
        reg_count: 2070
        include_count: 2070
        update_count: 0
        task_count: 2070

        date_last_sync: 2020-03-30 18:34:23
        upmost_last_update: 2020-01-25 13:11:33

        Execution time: 0:00:22.808

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2070
        reg_count: 2070
        include_count: 2070
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 2070

        date_last_sync: 2020-03-30 18:34:46
        upmost_last_update: 2020-01-25 13:11:33

        sequence_code: clv.lab_test.report.code
        sequence_number_next_actual: 2464

        Execution time: 0:03:06.326

        ########## clv.verification.marker (clv.verification.marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        external_objects: 19
        reg_count: 19
        include_count: 19
        update_count: 0
        task_count: 19

        date_last_sync: 2020-03-30 18:37:52
        upmost_last_update: 2019-10-15 22:19:14

        Execution time: 0:00:00.423

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 19
        reg_count: 19
        include_count: 19
        update_count: 0
        sync_include_count: 0
        sync_update_count: 0
        sync_count: 0

        task_count: 19

        date_last_sync: 2020-03-30 18:37:53
        upmost_last_update: 2019-10-15 22:19:14

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.764

        ############################################################
        Execution time: 1:03:48.140

.. _External Sync Batch - Default Batch - 20200330(2):

*External Sync Batch* - *Default Batch* (2) (Execution time: 0:08:21.340)
-------------------------------------------------------------------------

    ::

        ########## Default Batch ##########

        ########## res.country (res.country) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:38
        upmost_last_update: False

        Execution time: 0:00:00.266

        ########## res.country.state (res.country.state) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_recognize"...

        sync_objects: 8
        reg_count: 8
        include_count: 0
        task_count: 8

        date_last_sync: 2020-03-30 19:28:38
        upmost_last_update: 2019-06-11 14:34:36

        Execution time: 0:00:00.414

        ########## res.city (res.city) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:39
        upmost_last_update: False

        Execution time: 0:00:00.161

        ########## res.users (res.users) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:39
        upmost_last_update: False

        Execution time: 0:00:00.198

        ########## clv.global_tag (clv.global_tag) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:39
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.177

        ########## clv.phase (clv.phase) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:39
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.159

        ########## hr.department (hr.department) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:40
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.162

        ########## hr.job (hr.job) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:40
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.157

        ########## hr.employee (hr.employee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:40
        upmost_last_update: False

        sequence_code: hr.employee.code
        sequence_number_next_actual: 250

        Execution time: 0:00:00.217

        ########## hr.employee.history (hr.employee.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:40
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.206

        ########## clv.address.category (clv.address.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:40
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.182

        ########## clv.address (clv.address) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:40
        upmost_last_update: False

        sequence_code: clv.address.code
        sequence_number_next_actual: 705

        Execution time: 0:00:00.179

        ########## clv.address_aux (clv.address_aux) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:41
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.163

        ########## clv.address.history (clv.address.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:41
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.200

        ########## clv.family.category (clv.family.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:41
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.202

        ########## clv.family (clv.family) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:41
        upmost_last_update: False

        sequence_code: clv.family.code
        sequence_number_next_actual: 442

        Execution time: 0:00:00.189

        ########## clv.family.history (clv.family.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:41
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.181

        ########## clv.person.category (clv.person.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:42
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.163

        ########## clv.person.marker (clv.person.marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:42
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.161

        ########## clv.person (clv.person) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:28:42
        upmost_last_update: 2020-01-24 18:00:15

        sequence_code: clv.person.code
        sequence_number_next_actual: 1705

        Execution time: 0:00:19.143

        ########## clv.person.history (clv.person.history) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:01
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.186

        ########## clv.person_aux (clv.person_aux) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:01
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.183

        ########## survey.stage (survey.stage) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:02
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.186

        ########## survey.survey (survey.survey) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:02
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.179

        ########## survey.page (survey.page) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:02
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.186

        ########## survey.question (survey.question) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:02
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.180

        ########## survey.label (survey.label) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:29:02
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.180

        ########## survey.user_input (survey.user_input) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: False

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 3807
        reg_count: 3807
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 3807
        sync_count: 3807

        task_count: 3807

        date_last_sync: 2020-03-30 19:29:03
        upmost_last_update: 2020-01-24 23:11:25

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:04:20.388

        ########## clv.event (clv.event) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:23
        upmost_last_update: False

        sequence_code: clv.event.code
        sequence_number_next_actual: 34

        Execution time: 0:00:00.200

        ########## clv.event.attendee (clv.event.attendee) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:23
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.180

        ########## clv.document.category (clv.document.category) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:23
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.174

        ########## clv.document.type (clv.document.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:24
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.173

        ########## clv.document (clv.document) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:24
        upmost_last_update: False

        sequence_code: clv.document.code
        sequence_number_next_actual: 8674

        Execution time: 0:00:00.200

        ########## clv.lab_test.unit (clv.lab_test.unit) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:24
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.180

        ########## clv.lab_test.parasite (clv.lab_test.parasite) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:24
        upmost_last_update: False

        Execution time: 0:00:00.182

        ########## clv.lab_test.crystal (clv.lab_test.crystal) ##########
        method: _object_external_recognize

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:24
        upmost_last_update: False

        Execution time: 0:00:00.177

        ########## clv.lab_test.type (clv.lab_test.type) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:25
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.182

        ########## clv.lab_test.request (clv.lab_test.request) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:33:25
        upmost_last_update: False

        sequence_code: clv.lab_test.request.code
        sequence_number_next_actual: 5014

        Execution time: 0:00:00.199

        ########## clv.lab_test.result (clv.lab_test.result) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

        external_max_task: 200000
        external_disable_identification: True
        external_disable_check_missing: True
        external_disable_inclusion: False
        external_disable_sync: False
        external_last_update_args: []

        enable_sequence_code_sync: True

        login_msg: [01] Login Ok.

        Executing: "_object_external_sync"...

        sync_objects: 2070
        reg_count: 2070
        include_count: 0
        update_count: 0
        sync_include_count: 0
        sync_update_count: 2070
        sync_count: 2070

        task_count: 2070

        date_last_sync: 2020-03-30 19:33:25
        upmost_last_update: 2020-01-25 13:11:13

        sequence_code: clv.lab_test.result.code
        sequence_number_next_actual: 3137

        Execution time: 0:03:33.982

        ########## clv.lab_test.report (clv.lab_test.report) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:36:59
        upmost_last_update: False

        sequence_code: clv.lab_test.report.code
        sequence_number_next_actual: 2464

        Execution time: 0:00:00.201

        ########## clv.verification.marker (clv.verification.marker) ##########
        method: _object_external_sync

        external_host: https://192.168.25.183
        external_dbname: clvhealth_jcafb_2020

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

        date_last_sync: 2020-03-30 19:36:59
        upmost_last_update: False

        sequence_code: False
        sequence_number_next_actual: False

        Execution time: 0:00:00.182

        ############################################################
        Execution time: 0:08:21.340
