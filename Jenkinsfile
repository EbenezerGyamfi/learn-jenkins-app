pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
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
            agent {
                docker {
                    image 'node:18-alpine'
                }
            }
            steps {
                sh '''
                    ls
                    npm run test
                    find . -name '*.xml'
                '''
            }
        }

        stage('E2E') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.49.1-noble'
                }
            }
            steps {
                sh '''
                    npm install -g serve
                    serve -s build 
                    npx palywright test

                '''
            }
        }
    }

    post {
        always {
            junit 'test-results/**/*.xml'
        }
    }
}
