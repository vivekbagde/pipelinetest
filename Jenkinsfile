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
                  docker rmi projectdocker1203/jenkinspipeline
                  cd ..
                '''
            }
        }
        stage ('Push To DockerHub') {
            steps {
                dir (azure-vote/) {
                    script {
                        docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                            def image = docker.build('projectdocker1203:latest')
                            image.push()
                        }
                    }
                } 
            }
        }
    }
}
