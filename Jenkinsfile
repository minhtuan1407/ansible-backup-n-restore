pipeline {
    agent { label 'master' }
    options {
        ansiColor('vga')
    }
    parameters {
        string(name: 'ip_server', defaultValue: '', description: '')
        // choice(name: 'system_name', choices: ['CloudPBX', 'SBC', 'PitelPBX', 'Autocall', 'PitelCallCenter', 'BillingAST', 'BillingFS', 'ELK', 'Database', 'WebServer', 'LAB'], description: '')
        choice(name: 'task', choices: ['Backup', 'Restore'], description: '')
        // choice(name: 'web_service', choices: ['', 'Apache2', 'Nginx'], description: '')
        // choice(name: 'db_service', choices: ['', 'MariaDB', 'PostgreSQL'], description: '')
        // choice(name: 'voip_service', choices: ['', 'Asterisk', 'FreeSWITCH', 'Kamailio', 'OpenSIPs'], description: '')
        // choice(name: 'crontab_3h', choices: ['Yes', 'No'], description: '')
        // choice(name: 'run_now', choices: ['Yes', 'No'], description: '')
        booleanParam(name: 'Apache2', defaultValue: false, description: '')
        booleanParam(name: 'Nginx', defaultValue: false, description: '')
        booleanParam(name: 'MariaDB', defaultValue: false, description: '')
        booleanParam(name: 'PostgreSQL', defaultValue: false, description: '')
        booleanParam(name: 'Asterisk', defaultValue: false, description: '')
        booleanParam(name: 'FreeSWITCH', defaultValue: false, description: '')
        booleanParam(name: 'Kamailio', defaultValue: false, description: '')
        booleanParam(name: 'OpenSIPs', defaultValue: false, description: '')
        booleanParam(name: 'Asterisk', defaultValue: false, description: '')
        booleanParam(name: 'crontab_3h', defaultValue: true, description: '')
        booleanParam(name: 'run_now', defaultValue: true, description: '')
        string(name: 'rclone_path', defaultValue: '', description: '')
        string(name: 'backup_path', defaultValue: '/root/', description: '')
        string(name: 'recordings_path', defaultValue: '/usr/local/freeswitch/recordings/', description: '')
        string(name: 'custom_path_01', defaultValue: '', description: '')
        string(name: 'custom_path_02', defaultValue: '', description: '')
        string(name: 'custom_path_03', defaultValue: '', description: '')
    }
    stages {
        stage ("Check OS & Rclone") {
            steps {
                ansiblePlaybook (
                    playbook: '${WORKSPACE}/ansible-backup-n-restore.yml',
                    inventory: '${WORKSPACE}/hosts_all_server',
                    tags: 'check-os-n-rclone',
                    extraVars: [
                        ip_server: [value: '${ip_server}', hidden: false]
                    ]
                )
            }
        }
    }
}