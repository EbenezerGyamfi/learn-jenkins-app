pipeline {
    agent any

    stages {

         stage('Run Test') {
          
            parallel{
                 stage('stag 1') {
            steps {
                sh '''
                   echo Hello 
                '''
            }

            
        }

        stage('stag 2') {
            steps {
                sh '''
                   echo Hello 
                '''
            }

        }
            }
            steps {
                sh '''
                   
                '''
            }
        }
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
                    reuseNode true
                }
            }
            steps {
                sh '''
                   
                '''
            }
        }

         stage('stag 1') {
            steps {
                sh '''
                   echo Hello 
                '''
            }

            
        }

        stage('stag 2') {
            steps {
                sh '''
                   echo Hello 
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
