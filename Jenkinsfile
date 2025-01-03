pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                cleanWs()
                echo 'Building a new Laptop'
                sh 'mkdir -p build-1'
                sh 'touch build-1/computer.txt'
                sh 'echo "Mainboard" >> build-1/computer.txt'
                sh 'cat build-1/computer.txt'
            }
        }
    }
}