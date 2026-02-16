pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mogalgiddiv/simple-java-webapp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-creds',
                        url: 'http://localhost:8080',
                        path: '/simple-java-webapp'
                    )
                ],
                war: 'target/*.war'
            }
        }
    }
}
