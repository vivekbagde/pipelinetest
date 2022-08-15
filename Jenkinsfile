pipeline {
    agent any
    stages {
        stage ('verify branch') {
            steps {
                echo "verify $GIT_BRANCH"
            }
        }
        stage ('Docker Build') {
            steps {
                sh 'docker images -a'
                sh ```
                  cd azure-vote/
                  docker build -t projectdocker1203/jenkinspipeline .
                  docker images -a
                  cd ..
                  docker rmi projectdocker1203/jenkinspipeline
                ```
            }
        }
    }
}
