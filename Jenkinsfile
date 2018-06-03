#!/usr/bin/env groovy
 pipeline {
    agent any 
 //tools { 
   //     maven 'Maven 3.3.9' 
     //   jdk 'jdk8' 
    //}
    stages {
        stage ('Initialize') {
            steps {
                   sh '''
                    echo "PATH = ${PATH}"
                    //echo "M2_HOME = ${M2_HOME}"
                   '''  
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
             failure {
      // notify users when the Pipeline fails
          mail to: 'Balachandar_gurusamy@cable.comcast.com',
          subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
          body: "Something is wrong with ${env.BUILD_URL}"
               }
             
            }
        }
    
        stage('Notification') {
            steps {
                echo 'inside slack notification'
                // slackSend channel: SLACK_CHANNEL, color: 'good', message: env.BUILD_URL + ' deployment started '
             slackSend channel: '#visetest', color: 'good', message:'Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}',baseUrl:'https://cim.slack.com/services/hooks/jenkins-ci/',teamDomain: 'cim', token: 'ldhDuSiSkvnLEeFLUPyWndJF'
                //slackSend channel: "#channel-name", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
             }
    }
}
}

