pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/fkdkdsj/jenkins-docker-push-pipeline'
            }
        }
        stage('Build and push') {
            withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUsername')]) {
            }
        }
    }
}
