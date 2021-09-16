pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/fkdkdsj/jenkins-docker-push-pipeline'
            }
        }
        stage('Build and push') {
            //steps {
                //script {
                //    dockerImage = docker.build "ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}"
                //    docker.withRegistry("","dockerHub") {
                //        dockerImage.push()
                //    }
                //}
                //sh 'docker rmi "ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}"'
            //}
            withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUsername')]) {
                sh '''
                docker login -u ${dockerUsername} -p ${dockerPassword}
                docker build -t ${JOB_NAME##*/}:${BUILD_NUMBER} .
                docker image tag ${JOB_NAME##*/}:${BUILD_NUMBER} ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}
                docker push ldmoko/${JOB_BASE_NAME}:${BUILD_NUMBER}
                '''// some block
            }
        }
    }
}
