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
                    echo 'deploying docker image to EC2'
                    def dockerComposeCmd = "docker-compose -f docker-compose.yaml up --detach"
                    sshagent(['ec2-server-key']) {
                        sh "scp docker-compose.yaml ec2-user@ip-172-31-26-196:/home/ec2-user"
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@13.218.221.128 ${dockerCmd}"
                    }
                }

            }
        }
    }
}
