pipeline {
    agent any

    stages{
        stage('Code'){
            steps{
            git url: 'https://github.com/Stiwari2907/node-todo-cicdupdate.git', branch: 'master'
           }

        }
        stage('Build'){
            steps{
                sh 'docker build -t somadritiwari2907/nodetodo:latest .'
            }
        }
        stage('Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh 'docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}'
                    sh 'docker push somadritiwari2907/nodetodo:latest'
                }
            }
        }
    }
}
