pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Manual Approval') {
            steps {
                input message: 'Apakah Anda menyetujui lanjutan?', submitter: 'operators'
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
        stage('Delay Execution') {
            steps {
                script {
                    sleep time: 60, unit: 'SECONDS' 
                }
            }
        }
        stage('Terminate Application') {
            steps {
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
