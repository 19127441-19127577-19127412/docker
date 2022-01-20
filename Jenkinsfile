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
		bat "docker build -t test5:latest ."
		bat "docker tag test5:latest pdtien19/test5:latest"
            }
        }
        stage ("Publish") {
            steps {
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/'){
                    bat 'docker push pdtien19/test5:latest'
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
