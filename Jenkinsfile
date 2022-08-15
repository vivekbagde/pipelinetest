pipeline {
    agent any
    environment {
        imagename = "projectdocker1203/testing"
        registryCredential = 'dockerhub'
        dockerImage = ''
    }
    stages {
        stage ('verify branch') {
            steps {
                sh 'echo verify "$GIT_BRANCH"'
            }
        }
        stage ('Docker Build') {
            steps {
                script {
                  docker.withRegistry( 'https://index.docker.io/v1/', "$registryCredential" ) {
                     dockerImage.push("$BUILD_NUMBER")
                     dockerImage.push('latest')
                  }
                }
            }
        }
    }
}
