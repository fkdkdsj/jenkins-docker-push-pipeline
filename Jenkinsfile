pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/fkdkdsj/jenkins-docker-push-pipeline'
            }
        }
        stage('Build and push') {
            steps {
              sh 'docker build -t ${JOB_NAME##*/}:${BUILD_NUMBER} .'
              sh 'docker image tag ${JOB_NAME##*/}:${BUILD_NUMBER} ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}'
              sh 'docker push ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}'
            }
        }
    }
}
