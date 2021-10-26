pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        ./gradlew clean build

                        docker build -t spring-boot .
                    """
                }
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }
}