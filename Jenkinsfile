pipeline {
    agent { label 'master' }
    options {
        ansiColor('vga')
    }
    parameters {
        string(name: 'ip_server', defaultValue: '', description: '')
        choice(name: 'system_name', choices: ['CloudPBX', 'SBC', 'PitelPBX', 'Autocall', 'PitelCallCenter', 'BillingAST', 'BillingFS', 'ELK', 'Database', 'WebServer', 'LAB'], description: '')
        choice(name: 'system_name', choices: ['Backup', 'Restore'], description: '')
        booleanParam(name: 'crontab_3h', defaultValue: true, description: '')
        booleanParam(name: 'run_now', defaultValue: true, description: '')
        choice(name: 'web_service', choices: ['', 'Apache2', 'Nginx'], description: '')
        choice(name: 'db_service', choices: ['', 'MariaDB', 'PostgreSQL'], description: '')
        choice(name: 'voip_service', choices: ['', 'FreeSWITCH', 'Asterisk', 'Kamailio', 'OpenSIPs'], description: '')
        string(name: 'rclone_path', defaultValue: '', description: '')
        string(name: 'backup_path', defaultValue: '/root/', description: '')
        string(name: 'recordings_path', defaultValue: '/usr/local/freeswitch/recordings/', description: '')
        string(name: 'custom_path01', defaultValue: '', description: '')
        string(name: 'custom_path02', defaultValue: '', description: '')
        string(name: 'custom_path03', defaultValue: '', description: '')
    }
    stages {
        stage ("Check OS & Install rclone") {
            steps {
                echo "Hello TuanTuanTuan"
            }
        }
    }
}