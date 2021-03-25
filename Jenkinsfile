pipeline {
    agent any
    stages {
        stage('CleanWS') {
            steps {
                cleanWs()
            }
        }
        stage('Clone') {
            steps {
                git 'https://github.com/ngocngv/docker-hello-world-spring-boot.git'
            }
        }
        // stage('Unit Tests') {
        //     agent { docker { image 'maven:3.3.3' } }
        //     steps {
        //         sh 'mvn test '
        //     }
        // }
        stage('Build') {
            steps {
                sh 'docker build -t example-app .'
            }
        }
        stage('Push') {
            steps {
                sh 'docker tag example-app ngocng/example-app:latest'
                sh 'docker push ngocng/example-app:latest'
            }
        }
        // stage('Test') {
        //     steps {
        //         sh 'kubectl get nodes'
        //     }
        // }
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deploy'
            }
        }
    }
}
