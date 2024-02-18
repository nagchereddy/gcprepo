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
        
       stage('Building image & push') {
        steps{
            script{
      docker.withRegistry('${GCR_URL}', '${ARTIFACT_CREDS}') {

        def customImage = docker.build("${GCR_URL}/${APP_NAME}:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
            }
        }
    }
       
    
    
}
}