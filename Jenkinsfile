pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
        ARTIFACTORY_URL  = 'ramkumarpudi.jfrog.io'
        IMAGE_URL_WITH_TAG = "${ARTIFACTORY_URL}/simplewebapp:${DOCKER_TAG}"
    }
    stages{
    //stage('Git Code Checkout'){
//	    steps{
        
       // git credentialsId: 'GitHub', url: 'https://github.com/RAMKUMAR-devops/Assignment-task02.git'
	//git credentialsId: 'gitcred', url: 'https://github.com/RAMKUMAR-devops/Assignment-task02.git'
	//	    git credentialsId: 'git', url: 'https://github.com/RAMKUMAR-devops/Assignment-task02.git'
	//    }
    //}
	    stage('Build Docker Image'){
            steps{
                sh "docker build . -t ${IMAGE_URL_WITH_TAG}"
            }
        }
	    
    stage('Build Docker Image and Publish to JFrog docker registry'){
       steps{
        // withCredentials([string(credentialsId: 'nexus-pwd', variable: 'nexusPwd')]) {
           //       sh "docker login -u admin -p ${nexusPwd} ${NEXUS_URL}"
             //      sh "docker push ${IMAGE_URL_WITH_TAG}"
               //}
	   withCredentials([usernamePassword(credentialsId: 'jfrogcred', passwordVariable: 'jfrogpasswd', usernameVariable: 'jfroguser')]) {
		   sh "docker login -u ${jfroguser} -p ${jfrogpasswd} ${ARTIFACTORY_URL}"
                   sh "docker push ${IMAGE_URL_WITH_TAG}"
        }    
	   
       }

    //}
    //stage('Docker Deploy Dev'){
      //      steps{
        //        sshagent(['tomcat-dev']) {
          //          withCredentials([string(credentialsId: 'nexus-pwd', variable: 'nexusPwd')]) {
            //            sh "ssh ec2-user@172.31.0.38 docker login -u admin -p ${nexusPwd} ${NEXUS_URL}"
              //      }
					// Remove existing container, if container name does not exists still proceed with the build
		//			sh script: "ssh ec2-user@172.31.0.38 docker rm -f nodeapp",  returnStatus: true
                    
                  //  sh "ssh ec2-user@172.31.0.38 docker run -d -p 8080:8080 --name nodeapp ${IMAGE_URL_WITH_TAG}"
                //}
	  //  stage('scm'){
	//	    steps{
	
	    
	    //sh 'echo "hi" '
		    }
            }
        }
    }
    
    def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
    }
