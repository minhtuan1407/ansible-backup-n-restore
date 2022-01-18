pipeline {
    agent { label 'master' }
    options {
        ansiColor('vga')
    }
    parameters {
        string(name: 'ip_server', defaultValue: '', description: '')
        choice(name: 'system_name', choices: ['CloudPBX', 'SBC', 'PitelPBX', 'Autocall', 'PitelCallCenter', 'BillingAST', 'BillingFS', 'ELK', 'Database', 'WebServer', 'LAB'], description: '')
        string(name: 'rclone_path', defaultValue: '', description: '')
        choice(name: 'system_name', choices: ['Backup', 'Restore'], description: '')
        choice(name: 'crontab_3h', choices: ['Yes', 'No'], description: '')
        choice(name: 'run_now', choices: ['Yes', 'No'], description: '')
        choice(name: 'web_service', choices: ['', 'Apache2', 'Nginx'], description: '')
        choice(name: 'db_service', choices: ['', 'MariaDB', 'PostgreSQL'], description: '')
        choice(name: 'voip_service', choices: ['', 'FreeSWITCH', 'Asterisk', 'Kamailio', 'OpenSIPs'], description: '')
        string(name: 'backup_path', defaultValue: '', description: '/root/')
        string(name: 'recordings_path', defaultValue: '', description: '/usr/local/freeswitch/recordings/')
        choice(name: 'custom_path01', defaultValue: '', description: '')
        choice(name: 'custom_path02', defaultValue: '', description: '')
        choice(name: 'custom_path03', defaultValue: '', description: '')
    }
    stages {
        stage ("Check OS & Install rclone") {
            steps {
                echo "Hello TuanTuanTuan"
            }
        }
    }
}