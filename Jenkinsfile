pipeline {
    agent {
        docker {
            image 'node:18-alpine'
        }
    }

    
    stages {
        stage('Build') {
            steps {
                sh '''
                    pwd
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    test -f build/index.html
                    npm test
                '''
            }
        }
    }

    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
