pipeline {
    agent { label 'Jenkins_Node1' }
	
	environment {
          registry = "saikirangude12/hello-world"
          registryCredential = 'DockerHub'
	  latest = 'v5.0'
          dockerImage = ''
          PROJECT_ID = 'avi-new'
          CLUSTER_NAME = 'cluster-1'
          LOCATION = 'us-central1-c'
          CREDENTIALS_ID = 'avi-test'
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

	  stage('Clean Workspace') {
          steps{
            script {
              sh 'docker rmi saikirangude12/hello-world:latest'
          }
        }
      }
    }
}
