#!/usr/bin/env groovy
 pipeline {
    agent any 
    stages {
        stage('Init') {
            steps {
                echo 'Hello world!' 
                echo BUILD_NUMBER
                echo String.valueOf(currentBuild.timeInMillis)
            }
        }
        stage('Notification') {
            steps {
                echo 'inside slack notification'
                # slackSend channel: SLACK_CHANNEL, color: 'good', message: env.BUILD_URL + ' deployment started '
                slackSend channel: "#channel-name", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
             }
    }
}
}
