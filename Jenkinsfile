pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh './gradlew clean build'
                }
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
        stage('Build Docker') {
            steps {
                sh '''
                docker build -t spring-boot .

                docker login -u="pleum10" -p="p!eum77710"

                docker push spring-boot
                '''
            }
        }
    }
}
