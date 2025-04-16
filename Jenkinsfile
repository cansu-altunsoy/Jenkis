pipeline {
    agent any

    tools {
        maven 'Maven_3.9.9' // Jenkins global tool config'deki ismi bu olmalı
        jdk 'JDK_17' // Eğer JDK gerekiyorsa
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/cansu-altunsoy/Jenkis.git'
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
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}