pipeline 
{
    agent any 
    
    environment {
     url ="https://853219876644.dkr.ecr.us-east-2.amazonaws.com/"
     repoName="sikandar-repo"
     Tag="Maven_Image7"
     gitPath="https://github.com/sikandarqaisar/mavenApp.git"
    }
	stages {
     stage(‘Checkout’) {
	  steps {
	      script {
         git "${gitPath}"
	  }
	 }
	}
  	 stage (‘Build’) {
	  steps {
	      script{
            docker.build("${repoName}")
     	   }
	      }
        }
	 stage (‘deploy’) {
	  steps {
	      script {
           docker.withRegistry("${url}", 'ecr:us-east-2:a-cred'){
           docker.image("${repoName}").push("${Tag}")
            }    
           }
	      }
        }
  }
}
