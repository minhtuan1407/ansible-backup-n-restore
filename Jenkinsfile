pipeline {
    agent { label 'master' }
    options {
        ansiColor('vga')
    }
    parameters {
        string(name: 'ip_server', defaultValue: '', description: '')
        string(name: 'db_user', defaultValue: '', description: '')
        string(name: 'db_pass', defaultValue: '', description: '')
        // choice(name: 'system_name', choices: ['CloudPBX', 'SBC', 'PitelPBX', 'Autocall', 'PitelCallCenter', 'BillingAST', 'BillingFS', 'ELK', 'Database', 'WebServer', 'LAB'], description: '')
        choice(name: 'task', choices: ['backup', 'restore'], description: '')
        // choice(name: 'web_service', choices: ['', 'Apache2', 'Nginx'], description: '')
        // choice(name: 'db_service', choices: ['', 'MariaDB', 'PostgreSQL'], description: '')
        // choice(name: 'voip_service', choices: ['', 'Asterisk', 'FreeSWITCH', 'Kamailio', 'OpenSIPs'], description: '')
        // choice(name: 'crontab_3h', choices: ['Yes', 'No'], description: '')
        // choice(name: 'run_now', choices: ['Yes', 'No'], description: '')
        booleanParam(name: 'apache2', defaultValue: false, description: '')
        booleanParam(name: 'nginx', defaultValue: false, description: '')
        booleanParam(name: 'mariadb', defaultValue: false, description: '')
        booleanParam(name: 'postgresql', defaultValue: false, description: '')
        booleanParam(name: 'asterisk', defaultValue: false, description: '')
        booleanParam(name: 'freeswitch', defaultValue: false, description: '')
        booleanParam(name: 'kamailio', defaultValue: false, description: '')
        booleanParam(name: 'opensips', defaultValue: false, description: '')
        booleanParam(name: 'rtpengine', defaultValue: false, description: '')
        booleanParam(name: 'crontab_3h', defaultValue: true, description: '')
        booleanParam(name: 'run_now', defaultValue: true, description: '')
        booleanParam(name: 'delete_after', defaultValue: false, description: '')
        booleanParam(name: 'restart_after', defaultValue: false, description: '')
        string(name: 'rclone_url', defaultValue: 'minhtuan.tel4vn.com', description: '')
        string(name: 'backup_restore_path', defaultValue: '/opt/backup/', description: '')
        string(name: 'recordings_path', defaultValue: '', description: '')
        string(name: 'custom_path_01', defaultValue: '', description: '')
        string(name: 'custom_path_02', defaultValue: '', description: '')
        string(name: 'custom_path_03', defaultValue: '', description: '')
    }
    stages {
        stage ("Install Rclone") {
            steps {
                ansiblePlaybook (
                    playbook: '${WORKSPACE}/ansible-backup-n-restore.yml',
                    inventory: '${WORKSPACE}/hosts_all_server',
                    tags: 'install-rclone',
                    extraVars: [
                        ip_server: [value: '${ip_server}', hidden: false]
                    ]
                )
            }
        }
        stage ("Backup") {
            steps {
                ansiblePlaybook (
                    playbook: '${WORKSPACE}/ansible-backup-n-restore.yml',
                    inventory: '${WORKSPACE}/hosts_all_server',
                    tags: 'backup',
                    extraVars: [
                        ip_server: [value: '${ip_server}', hidden: false],
                        db_user: [value: '${db_user}', hidden: true],
                        db_pass: [value: '${db_pass}', hidden: true],
                        task: [value: '${task}', hidden: false],
                        apache2: [value: '${apache2}', hidden: false],
                        nginx: [value: '${nginx}', hidden: false],
                        mariadb: [value: '${mariadb}', hidden: false],
                        postgresql: [value: '${postgresql}', hidden: false],
                        asterisk: [value: '${asterisk}', hidden: false],
                        freeswitch: [value: '${freeswitch}', hidden: false],
                        kamailio: [value: '${kamailio}', hidden: false],
                        opensips: [value: '${opensips}', hidden: false],
                        rtpengine: [value: '${rtpengine}', hidden: false],
                        crontab_3h: [value: '${crontab_3h}', hidden: false],
                        run_now: [value: '${run_now}', hidden: false],
                        delete_after: [value: '${delete_after}', hidden: false],
                        restart_after: [value: '${restart_after}', hidden: false],
                        rclone_url: [value: '${rclone_url}', hidden: false],
                        backup_restore_path: [value: '${backup_restore_path}', hidden: false],
                        recordings_path: [value: '${recordings_path}', hidden: false],
                        custom_path_01: [value: '${custom_path_01}', hidden: false],
                        custom_path_02: [value: '${custom_path_02}', hidden: false],
                        custom_path_03: [value: '${custom_path_03}', hidden: false]
                    ]
                )
            }
        }
        stage ("Restore") {
            steps {
                ansiblePlaybook (
                    playbook: '${WORKSPACE}/ansible-backup-n-restore.yml',
                    inventory: '${WORKSPACE}/hosts_all_server',
                    tags: 'restore',
                    extraVars: [
                        ip_server: [value: '${ip_server}', hidden: false],
                        db_user: [value: '${db_user}', hidden: true],
                        db_pass: [value: '${db_pass}', hidden: true],
                        task: [value: '${task}', hidden: false],
                        apache2: [value: '${apache2}', hidden: false],
                        nginx: [value: '${nginx}', hidden: false],
                        mariadb: [value: '${mariadb}', hidden: false],
                        postgresql: [value: '${postgresql}', hidden: false],
                        asterisk: [value: '${asterisk}', hidden: false],
                        freeswitch: [value: '${freeswitch}', hidden: false],
                        kamailio: [value: '${kamailio}', hidden: false],
                        opensips: [value: '${opensips}', hidden: false],
                        rtpengine: [value: '${rtpengine}', hidden: false],
                        crontab_3h: [value: '${crontab_3h}', hidden: false],
                        run_now: [value: '${run_now}', hidden: false],
                        delete_after: [value: '${delete_after}', hidden: false],
                        restart_after: [value: '${restart_after}', hidden: false],
                        rclone_url: [value: '${rclone_url}', hidden: false],
                        backup_restore_path: [value: '${backup_restore_path}', hidden: false],
                        recordings_path: [value: '${recordings_path}', hidden: false],
                        custom_path_01: [value: '${custom_path_01}', hidden: false],
                        custom_path_02: [value: '${custom_path_02}', hidden: false],
                        custom_path_03: [value: '${custom_path_03}', hidden: false]
                    ]
                )
            }
        }
    }
    post {
        always {
            // emailext subject: 'Jenkins ${BUILD_STATUS} [#${BUILD_NUMBER}] - ${PROJECT_NAME}',
            // body: '''Build <a href="$PROJECT_URL">$PROJECT_NAME</a> <br>
            // Build Number <a href="$BUILD_URL">$BUILD_NUMBER</a> result with status: <b>$BUILD_STATUS</b> <br>
            // <a href="$BUILD_URL/console">Build log</a> on host ${ip_server}''',
            // to: 'tech@tel4vn.com'

            telegramSend(message: '''Build [$PROJECT_NAME]($PROJECT_URL) \nBuild Number [$BUILD_NUMBER]($BUILD_URL) result with status: *$BUILD_STATUS* \n[Build log]($BUILD_URL/console) on host ${ip_server}''',
            chatId:1284662325)
        }
    }
}