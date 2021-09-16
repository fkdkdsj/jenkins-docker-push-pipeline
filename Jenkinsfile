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
                container('ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}') {
                  // some block
                }
            }
        }
    }
}
