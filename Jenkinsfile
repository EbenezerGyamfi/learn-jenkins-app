pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
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

        stage('Test'){
            agent{
                docker {
                    image 'node:18-alpine'
                }
            }
            steps{
                sh '''

                    ls
                    npm run test
                    find . -name '*.xml' # Locate JUnit XML files


                    '''
            }
        }
    }

    post {
        always {
            junit './test-results/junit.xml'
        }
    }
}