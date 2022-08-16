pipeline {
    agent any
    environment {
        dockerhub=credentials('dockerhub')
    }
    stages {
        stage ('verify branch') {
            steps {
                echo "verify $GIT_BRANCH"
            }
        }
        stage ('Docker Build') {
                when {
                    branch "master"
                }
                steps {
                    sh 'docker build -t projectdocker1203:$BUILD_NUMBER ./azure-vote'
                }
        }
        stage ('Push To DockerHub') {
            when {
                branch "master"
            }
            steps {
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                sh 'docker push projectdocker1203:$BUILD_NUMBER'
            }
        }
    }
}
