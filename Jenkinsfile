pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/PiotrKopec10/KolosJenkins.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
            post {
                always {
                    junit 'test-results/*.xml'
                }
            }
        }
        stage('Static Analysis') {
            steps {
                sh 'npm run lint'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            cleanWs()
        }
    }
}
