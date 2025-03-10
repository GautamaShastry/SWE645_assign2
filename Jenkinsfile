// Group: Alpha1 (Example)
// File: Jenkinsfile
// Description: CI/CD pipeline with Docker build/push, Kubernetes deploy, and post actions

pipeline {
    agent any
    
    environment {

        DOCKERHUB_CREDENTIALS = credentials('docker-credentials')
        
        // Timestamp for tagging the Docker image
        BUILD_TIMESTAMP = "${new Date().format('yyyyMMddHHmmss')}"

        KUBECONFIG_CREDENTIALS = credentials('kubeconfig')
    }
    
    stages {
        stage("Build Survey Image") {
            steps {
                script {
                    // Fetch the current SCM and print the timestamp
                    checkout scm
                    sh 'echo ${BUILD_TIMESTAMP}'
                    
                    // Correctly login to DockerHub using the username and password
                    sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
                    
                    // Build the Docker image
                    def customImage = docker.build("gautam26/hw2-docker-image:${BUILD_TIMESTAMP}")
                }
            }
        }
        stage("Push img to docker hub") {
            steps {
                script {
                    // Push the Docker image to DockerHub
                    sh "docker push gautam26/hw2-docker-image:${BUILD_TIMESTAMP}"
                }
            }
        }
        
        stage("Deploy to kubernetes") {
			steps {
                withEnv(["KUBECONFIG=${KUBECONFIG_CREDENTIALS}"]) {
                    sh 'kubectl set image deployment/deployment container-hw2=gautam26/hw2-docker-image:${BUILD_TIMESTAMP} -n default'
                }
            }
        }
    }
    
    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed.'
        }
        always {
            echo 'Cleaning Up ...'
        }
    }
}
