#!/usr/bin.env groovy

pipeline {
    agent any
    stages {
        stage("Test") {
            steps {
                script {
                    echo "Testing the application..."
                    
                }               
                
            }
        }

        stage("Build") {
            steps {
                script {
                    echo "Building the application..."
                }               
            }
        }

        stage("Deploy") {
            steps {
                script{
                    def dockerCmd = 'docker run -p 3080:3080 -d amadeusmachina/demo-app:1.0'
                    sshagent(['ec2-server-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@13.218.221.128 ${dockerCmd}"
                    }
                }                
                
            }
        }
    }
}
