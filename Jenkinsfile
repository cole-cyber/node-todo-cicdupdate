pipeline {
    agent any
    stages{
        stage('Code'){
            steps{
            git url: 'https://github.com/cole-cyber/node-todo-cicdupdate.git', branch: 'Master'
            }
    }
        stage('Build'){
            steps{
            sh 'docker build -t coledocker11/nodetodo:latest .'
        }
    }
        stage('Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	     sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                     sh 'docker push coledocker11/nodetodo:latest'
                }
            }
        }
    }
}
