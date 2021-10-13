pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
        NEXUS_URL  = "172.31.34.232:8080"
        IMAGE_URL_WITH_TAG = "${NEXUS_URL}/node-app:${DOCKER_TAG}"
    }
    stages{
    stage{
    }stage('Git Code Checkout'){
        git credentialsId: 'GitHub', url: 'https://github.com/RAMKUMAR-devops/verizoncicd.git'
    }
    
    stage{
    }
    }
