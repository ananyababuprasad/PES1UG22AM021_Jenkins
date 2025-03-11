pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/ananyababuprasad/PES1UG22AM021_Jenkins.git']]
                ])
            }
        }
        stage('Build') {
            steps {
                script {
                    build 'PES1UG22AM021-1'
                    sh 'g++ main.cpp -o output'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh './output'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
    post {
        failure {
            script {
                echo 'Pipeline failed'
                error 'Stopping pipeline due to failure.'
            }
        }
    }
}
