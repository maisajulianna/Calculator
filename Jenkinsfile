
pipeline {
    agent any
    tools {
        maven 'Maven3'
        jdk 'JDK-21'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/maisajulianna/Calculator.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco execPattern: '**/target/jacoco.exec'
        }
    }
}

