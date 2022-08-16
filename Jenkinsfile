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
                when {
                    branch "$GIT_BRANCH"
                }
                steps {
                    sh 'docker build -t projectdocker1203:$BUILD_NUMBER ./azure-vote'
                }
        }
        stage ('Push To DockerHub') {
            when {
                branch "$GIT_BRANCH"
            }
            steps {
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                sh 'docker push projectdocker1203:$BUILD_NUMBER'
            }
        }
    }
}
