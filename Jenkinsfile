pipeline{
     agent any
	 
	 stages{
	    stage('Build'){
	        steps{
			     sh 'mvn clean package'
			}
			post{
			    success{
				    echo "Archiving the Artifacts"
					archiveArtifacts: '**/target/*.war'
				}
			}
	    }
		 stage('Deploy to tomcat server'){
	        steps{
			    deploy adapters: [tomcat9(credentialsId: '0ba0a1b4-2759-4306-80c5-b155c37cacb4', path: '', url: 'http://localhost:8181')], contextPath: null, war: '**/*.war'
			}
	    }
	 }
}
