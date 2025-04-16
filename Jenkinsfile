pipeline {
    agent any

    environment {
        MAVEN_OPTS = '-Dmaven.test.failure.ignore=false'
        MAVEN_HOME = 'C:\\Program Files\\apache-maven-3.9.9'  // Maven'ın doğru kurulum yolu
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-17'  // Java'nın doğru kurulum yolu
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/cansu-altunsoy/Jenkis.git', credentialsId: 'dc56b904-2c60-4991-91e7-e86def0e981b'
            }
        }

        stage('Build & Test') {
            steps {
                echo 'Running Maven tests with tag @test03'
                bat "mvn clean test -Dcucumber.filter.tags='@test03'"
            }
        }

        stage('Generate Allure Report') {
            steps {
                allure includeProperties: false, jdk: '', results: [[path: 'target/allure-results']]
            }
        }

        stage('Push to GitHub') {
            steps {
                echo 'Tests passed, pushing to GitHub...'
                withCredentials([usernamePassword(credentialsId: 'dc56b904-2c60-4991-91e7-e86def0e981b', usernameVariable: 'GIT_USER', passwordVariable: 'GIT_PASS')]) {
                    bat """
                        git config --global user.email "jenkins@example.com"
                        git config --global user.name "Jenkins CI"
                        git remote set-url origin https://${GIT_USER}:${GIT_PASS}@github.com/cansu-altunsoy/Jenkis.git
                        git add .
                        git commit -m "Automated commit by Jenkins after successful build" || echo "Nothing to commit"
                        git push origin master
                    """
                }
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml' // Surefire raporlarını al
        }
    }
}
