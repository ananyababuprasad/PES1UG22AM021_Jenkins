pipeline {
    agent any
    stages [
        stage ('clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                branches: [[name: '*/main']],
                userRemoteConfigs: [[url: 'https://github.com/ananyababuprasad/PES1UG22AM021_Jenkins.git']]
            ])
            }
        }
        stage('Build') {
            steps {
                build 'PES1UG22AM021-1'
                sh 'g++ main.cpp -o output'
            }
        }
        stage('Test') {
            steps {
                sh './output'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    ]
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
