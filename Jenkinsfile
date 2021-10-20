pipeline {
    agent any
    environment{
      
        ARTIFACTORY_URL  = 'ramkumarpudi.jfrog.io'
	APP_NAME = 'task'
    
    }
    stages{
   
	    stage('Build and tag Docker Image'){
            steps{
		   
		    sh "docker build . -t ${APP_NAME}"
		    sh "docker tag ${APP_NAME} ${ARTIFACTORY_URL}/simplewebapp/${APP_NAME}:latest"
          
            }
        }
	    
    stage('Publish Docker image to JFrog docker registry'){
       steps{
       
	   withCredentials([usernamePassword(credentialsId: 'jfrogcred', passwordVariable: 'jfrogpasswd', usernameVariable: 'jfroguser')]) {
		   sh "docker login -u ${jfroguser} -p ${jfrogpasswd} ${ARTIFACTORY_URL}"
		   sh "docker push ${ARTIFACTORY_URL}/simplewebapp/${APP_NAME}:latest"
                 
        }    
	   
       }
    }
	    stage('Deployment in kubernetes cluster'){
		    steps{
			sshagent(['ssh-jerkins-user']) {
                                sh 'scp -o StrictHostKeyChecking=no deployment.yml service.yml root@34.224.174.254:/root'
				//sh 'ls -la'
                    script{
                         try{
                           sh 'ssh root@34.224.174.254 kubectl create -f deployment.yml'
	                   sh 'ssh root@34.224.174.254 kubectl create -f service.yml'
                             }
			 catch(error)
                           {
	                   sh 'ssh root@34.224.174.254 kubectl apply -f deployment.yml'
	                   sh 'ssh root@34.224.174.254 kubectl apply -f service.yml'
                            }
                  }    
			 	    
	      }
	    }
	    
            }
        }
    }
    
  
