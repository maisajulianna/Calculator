
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
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                 bat 'mvn test'
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

