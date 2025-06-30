pipeline {
    agent any

    stages {
        stage('Update System') {
            steps {
                echo 'Updating package list...'
                sh 'sudo apt-get update -y'

                echo 'Upgrading installed packages...'
                sh 'sudo apt-get upgrade -y'
            }
        }

        stage('Install Apache') {
            steps {
                echo 'Installing Apache web server...'
                sh 'sudo apt-get install apache2 -y'

                echo 'Checking Apache status...'
                sh 'systemctl status apache2'
            }
        }

        stage('Running script') {
            steps {
                echo 'Setting correct permissions for script...'
                sh 'chmod +x check-codes-apachelog'

                echo 'Checking for 4xx and 5xx errors in logs...'
                sh './check-codes-apachelog'
            }
        }
    }
}