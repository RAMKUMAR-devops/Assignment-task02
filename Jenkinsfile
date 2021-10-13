pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
        ARTIFACTORY_URL  = 'ramkumarpudi.jfrog.io'
        IMAGE_URL_WITH_TAG = "${ARTIFACTORY_URL}/simplewebapp:${DOCKER_TAG}"
    }
    stages{
    stage('Git Code Checkout'){
        
        git credentialsId: 'GitHub', url: 'https://github.com/RAMKUMAR-devops/Assignment-task02.git'
    }
    stage('Build Docker Image and Publish to JFrog docker registry'){
      //  appname = 'simplewebapp'
       // artifactory_repo = 'ramkumarpudi.jfrog.io'
             sh "docker build . -t ${IMAGE_URL_WITH_TAG}"
            // sh "docker build . -t ${appname}"
            // sh "docker tag ${appname} ${artifactory_repo}/${appname}:latest"
            // sh "docker login -u admin -p !QAZ1qaz ${artifactory_repo}"
            // sh "docker push ${artifactory_repo}/${appname}:latest"
             sh "docker login -u ramkumar.pudi@gmail.com -p !QAZ1qaz ${ARTIFACTORY_URL}"
             sh "docker push ${IMAGE_URL_WITH_TAG}"


    }
    stage{
    }
    }
    def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}
