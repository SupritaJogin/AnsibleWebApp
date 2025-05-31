pipeline {
    agent any
    environment {
        LANG = 'en_US.UTF-8'
        LC_ALL = 'en_US.UTF-8'
    }
    tools {
        maven 'Maven'  // Match your Jenkins Maven tool name
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SupritaJogin/AnsibleWebApp.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                bat 'wsl ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'


            }
        }
    }
} 
