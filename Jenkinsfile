pipeline {
	agent any
	stages {
		stage('running image on docker') {
			steps {
				sshagent(['10.0.143.117']) {
				
				sh """ssh -o StrictHostKeyChecking=no ec2-user@10.0.143.117 << EOF   
          sudo docker stop productservice
          sudo docker rm productservice
          sudo docker pull js194/productservice:latest
          sudo docker run -d -p 9000:9000 --restart unless-stopped --name productservice js194/productservice:latest
          exit
				EOF"""
				    
				}
			}
		}
	}
}
