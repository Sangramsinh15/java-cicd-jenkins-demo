pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'
        jdk 'JDK 11'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Sangramsinh15/java-cicd-jenkins-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy logic goes here.'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml' // Ensure test reports are generated in this path
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        }
    }
}
