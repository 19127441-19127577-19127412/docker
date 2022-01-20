pipeline {
    agent any
    stages {
        stage('gitclone') {

			steps {
				git branch: 'main', url: 'https://github.com/19127441-19127577-19127412/docker.git'
			}
		}
        stage ("Build") {
            steps {
		bat "docker build -t test_2:latest ."
		bat "docker tag test_2:latest pdtien19/test_2:latest"
            }
        }
        stage ("Publish") {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: ''){
                    bat 'docker push pdtien19/test_2:latest'
            }
        }
        }
    }

    post {
		always {
			bat 'docker logout'
		}
	}

}
