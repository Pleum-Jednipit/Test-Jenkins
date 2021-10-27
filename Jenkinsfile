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
                docker build -t localimage .

                docker login -u="pleum10" -p="p!eum77710"

                docker tag localimage:latest pleum10/spring-boot:firstimage

                docker push pleum10/spring-boot:firstimage
                '''
            }
        }
    }
}
