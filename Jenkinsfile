#!/usr/bin/env groovy
pipeline {
    agent any 
    stages {
        stage('Stage 1') {
            steps {
                echo 'Hello world!' 
                echo BUILD_NUMBER
                echo currentBuild.result
            }
        }
    }
}
