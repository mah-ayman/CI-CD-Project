pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                sh 'docker run -d ahmedeldaly097/CI-CD-Project .'
            }
        }
        stage('artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'pass', usernameVariable: 'username')]){
                sh 'docker login -u ${username} -p ${pass}'
                sh 'docker push ahmedeldaly097/web_app'
            }
           }
        }
        stage('deploy') {
            steps {
                sh 'docker run -d -p 5000:80 --name web_app ahmedeldaly097/web_app'
            }
        }
    }
}
