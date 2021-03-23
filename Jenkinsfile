pipeline {
        environment {
        imagename = "shir/mynode"
        registryCredential = 'dockerhub'
        dockerImage = ''
        }
        agent any
        stages {
            stage('Cloning Git') {
            steps {
            git branch: 'main', changelog: false, poll: false, url: 'https://github.com/shirsendu1234/dockerwebapp.git'
            }
        }
        stage('Building image') {
            steps{
            script {
            dockerImage = docker.build imagename
            }
           }
        }
        stage('Deploy Image') {
            steps{
            script {
            docker.withRegistry( '', registryCredential ) {
            //dockerImage.push("$BUILD_NUMBER")
            dockerImage.push('latest')
            }
           }
         }
        }
        stage('Remove Unused docker image') {
            steps{
            //sh "docker rmi $imagename:$BUILD_NUMBER"
            sh "docker rmi $imagename:latest"
            }
        }
        }
}
