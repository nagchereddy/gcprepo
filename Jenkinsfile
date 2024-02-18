pipeline{
    agent any
    environment{
        REPO_CREDS = 'github'
        ARTIFACT_CREDS = 'jenkinsogcp'
        GITHUB_NAME = 'gcprepo'
        GCR_URL = 'us-east1-docker.pkg.dev/solid-antler-409714/gcprepo'
        APP_NAME = 'httpd'
    }
    stages{
        stage("Checkout code"){
            steps{
                checkout scm
            }
            
        }
        stage("docker build"){
            steps{
                sh("docker build  -t ${GCR_URL}/${APP_NAME}:${env.BUILD_NUMBER} .")
            }
        }
    }
    
}