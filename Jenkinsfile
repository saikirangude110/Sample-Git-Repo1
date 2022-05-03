pipeline {
    agent { label 'Jenkins_Node1' }
	
	environment {
		registry = "saikirangude12/hello-world"
		PROJECT_ID = 'jenkins-296812'
                CLUSTER_NAME = 'k8s-cluster'
                LOCATION = 'us-central1-c'
                CREDENTIALS_ID = 'kubernetes'		
	           }
	
    stages {
	  stage('Building image') {
          steps {
		    script {
		    dockerImage = docker.build registry + ":latest"
	        }
	    }
        }
	    
	  stage('Deploy Image') {
          steps{
            script {
             docker.withRegistry( '', registryCredential ) {
             dockerImage.push()
          }
        }
      }
    }

    }
}
