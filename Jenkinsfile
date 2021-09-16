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
              sh '''
              docker login -uldmoko -pmima890216
              docker build -t ${JOB_NAME##*/}:${BUILD_NUMBER} .
              docker image tag ${JOB_NAME##*/}:${BUILD_NUMBER} ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}
              docker push ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}
              '''
            }
        }
    }
}
