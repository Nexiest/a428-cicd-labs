node {
    docker.image('node:16-buster-slim').inside("-p 3000:3000") {
        stage('Build') {
            try {
                sh 'npm install'
            } catch (Exception e) {
                currentBuild.result = 'FAILURE'
                error "Build failed: ${e.message}"
            }
        }

        stage('Test') {
            try {
                sh './jenkins/scripts/test.sh'
            } catch (Exception e) {
                currentBuild.result = 'FAILURE'
                error "Tests failed: ${e.message}"
            }
        }
    }
}
