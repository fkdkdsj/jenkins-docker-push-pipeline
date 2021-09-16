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
                script {
                    dockerImage = docker.build "ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}"
                    docker.withRegistry("","dockerHub") {
                        dockerImage.push()
                    docker rmi "ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}"
                    }
                }
            }
        }
    }
}
