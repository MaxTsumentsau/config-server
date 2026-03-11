pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'develop',
                    credentialsId: 'github-token',
                    url: 'https://github.com/MaxTsumentsau/config-server.git'
            }
        }

        stage('Build') {
            steps {
                bat '.\\gradlew.bat clean build -x test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t max2ba/config-server:latest D:/JavaProjects/config-server'
            }
        }

        stage('Docker Restart') {
            steps {
                bat '''
                cd /d D:\\JavaProjects\\config-server
                docker compose up -d --build config-server
                '''
            }
        }
    }
}

