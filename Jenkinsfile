pipeline {
    agent any

    stages{
        stage('Code'){
            steps{
            git url: 'https://github.com/alosie/node-todo-cicdupdate.git', branch: 'master'
           }

        }
        stage('Build'){
            steps{
                sh 'docker build -t alosie/node-todo-test:latest .'
            }
        }
        stage('Push'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh 'docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}'
                    sh 'docker push alosie/node-todo-test:latest'
                }
            }
        }
      stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
}

}
