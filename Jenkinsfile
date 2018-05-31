#!/usr/bin/env groovy
pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
                echo BUILD_NUMBER
                echo timeInMillis
            }
        }
        stage('Notification') {
            steps{
                echo 'inside slack notification'
                slackSend channel: "#balag", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
            }
    }
}
