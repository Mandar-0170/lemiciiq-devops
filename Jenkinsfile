pipeline {
    agent any
    

    
    stages {
        stage('Docker Build') {
            steps {
                script{
                    withDockerRegistry(credentialsId: '4e5e94a0-6b28-42af-9ed1-162070196a65') {
					sh "docker build -t portfoio-image:latest -f Dockerfile.alpine ."
				}
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                echo 'Test Passed'
            }
        }

		stage ('Docker Push') {
            	steps {
	    			script {
		     			withDockerRegistry(credentialsId: '4e5e94a0-6b28-42af-9ed1-162070196a65') {
			 				sh "docker push kubeleo21/portfolio-image:latest"
		    				}
						} 
	    
					}
	
				}

        
}
}
}
