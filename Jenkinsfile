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
    }
    
        post{
          
                echo 'inside slack notification'
                // slackSend channel: SLACK_CHANNEL, color: 'good', message: env.BUILD_URL + ' deployment started '
              success {
            slackSend channel: '#visetest',color: 'good', message: "SUCCESS: ${JOB_NAME} ${BUILD_NUMBER},baseUrl:'https://cim.slack.com/services/hooks/jenkins-ci/',teamDomain: 'cim', token: 'ldhDuSiSkvnLEeFLUPyWndJF'"
        }
        failure {
            slackSend channel: '#visetest',color: '#ea0017', message: "FAILURE: ${JOB_NAME} ${BUILD_NUMBER}. See the results here: ${BUILD_URL},baseUrl:'https://cim.slack.com/services/hooks/jenkins-ci/',teamDomain: 'cim', token: 'ldhDuSiSkvnLEeFLUPyWndJF'"
        }
        unstable {
            slackSend channel: '#visetest',color: '#ffb600', message: "UNSTABLE: ${JOB_NAME} ${BUILD_NUMBER}. See the results here: ${BUILD_URL},baseUrl:'https://cim.slack.com/services/hooks/jenkins-ci/',teamDomain: 'cim', token: 'ldhDuSiSkvnLEeFLUPyWndJF'"
        }
             //slackSend channel: '#visetest', color: 'good', message:'Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}',baseUrl:'https://cim.slack.com/services/hooks/jenkins-ci/',teamDomain: 'cim', token: 'ldhDuSiSkvnLEeFLUPyWndJF'
                //slackSend channel: "#channel-name", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
            
    
}
}

