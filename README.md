# Assignment-task02
Write pipeline-as-code to deploy containerised application. You can choose any sample application written in java, nodejs or php.  
Solution:  
Services/Tools used:  
1.Jenkins. 
2.Docker.  
3.Kubernetes.  
4.AWS EC2 servers.  
5.Jfrog artifactory.  
Steps:  
1.Create a sample index.html to deploy in apache server.  
2.Create Jenkinsfile of declarative pipeline with stages Build and tag docker image ,Push docker image to Jfrog artifactory,deploy the docker image in kubernetes cluster.
<img width="1133" alt="updated jenkins" src="https://user-images.githubusercontent.com/59164612/137919131-08ccbdd0-0afa-4f4d-8a02-686b69d939cb.png">
<img width="1133" alt="updatedjenkins2" src="https://user-images.githubusercontent.com/59164612/137919239-cabc8d89-0a42-4ac2-8764-7fd3b97a6806.png">
  i.Create webhook in github inorder to build the respective jenkins pipline whenever commit happens in github.
  <img width="1680" alt="github-webhook" src="https://user-images.githubusercontent.com/59164612/137497555-59bfc3dc-b996-4d2d-ad62-0e217a3dc4a0.png">
3.Create the kubernetes cluster in aws console using kops method.
<img width="1680" alt="kuberenetes cluster" src="https://user-images.githubusercontent.com/59164612/137498133-5dc7b3f4-08db-457c-9f2d-585539eecfe1.png">
4.Create Jfrog artifcatory of type Docker to store the built docker image from jenkins .
<img width="1680" alt="docker image" src="https://user-images.githubusercontent.com/59164612/137497338-32d48dca-bac5-4928-83b3-f05431041a5c.png">
5.Create deployment.yml and service.yml file to deploy the pod of docker image and to expose it to outside world.
<img width="1680" alt="terminal output" src="https://user-images.githubusercontent.com/59164612/137497692-8ccbc079-1ff2-4e02-94f9-728aacb3367e.png">
6.Accesing the pod from the browser using masternode ip along with nodeport.
<img width="1680" alt="app in browser" src="https://user-images.githubusercontent.com/59164612/137497793-f5d5763c-a543-4e0b-a82b-385fa84a6c9c.png">


