pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'  // Jenkins'te tanımlı bir Maven versiyonu
        jdk 'Java 17'        // JDK versiyonu sizin projeye göre
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/cansu-altunsoy/Jenkis.git'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Generate Allure Report') {
            steps {
                allure includeProperties: false, jdk: '', results: [[path: 'target/allure-results']]
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}