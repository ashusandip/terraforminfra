pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                    sh 'docker build -t your-image-name:tag .'
                }
            }
  
		stage('Unit Tests') {
			steps {
				sh 'npm test'  
			}
		}

		stage('Integration Tests') {
			steps {
				sh 'npm run integration-test'  
			}
		}
		stage('Deploy Infrastructure') {
			steps {
				sh 'terraform init && terraform apply -auto-approve'
			}
		}
		stage('Configure Instances') {
			steps {
				sh 'ansible-playbook -i inventory.ini playbook.yml'  
			}
		}


    }
}
