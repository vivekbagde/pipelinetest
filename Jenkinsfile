pipeline {
    agent any
    stages {
        stage ('verify branch') {
            steps {
                sh 'echo verify "$GIT_BRANCH"'
            }
        }
        stage ('Docker Build') {
            steps {
                sh 'docker images -a'
                sh '''
                  cd azure-vote/
                  docker build -t projectdocker1203/jenkinspipeline .
                  docker images -a
                '''
            }
        }
        stage ('Push To DockerHub') {
            steps {
                sh 'pwd'
            }
        }
    }
}
