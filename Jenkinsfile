pipeline {
    agent any
    environment {
        dockerhub=credentials('dockerhub')
    }
    stages {
        stage ('verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage ('Docker Build') {
                steps {
                    sh 'docker build -t projectdocker1203/test:$BUILD_NUMBER ./azure-vote'
                }
        }
        stage ('Push To DockerHub') {
            steps {
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                sh 'docker push projectdocker1203/test:$BUILD_NUMBER'
		sh 'docker rmi projectdocker1203/test:$BUILD_NUMBER'
            }
        }
    }
    post {
		always {
			sh 'docker logout'
		}
	}
}
