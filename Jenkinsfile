pipeline{
    agent any
    stages{
        stage("Checkout code"){
            steps{
                checkout scm
            }
            
        }
        stage("docker build"){
            steps{
                script{
                    myapp = docker.build("us-east1-docker.pkg.dev/solid-antler-409714/gcprepo/httpd:${env.BUILD_ID}")
                }
            }
        }
    }
    
}