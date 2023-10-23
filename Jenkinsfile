pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'

                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {

            }
        }
    }

    post {
        success {
            echo 'Pipeline selesai tanpa kesalahan. Menjalankan langkah deploy...'
        }
        failure {
            echo 'Pipeline gagal. Tidak ada langkah deploy yang dijalankan.'
        }
    }
}
