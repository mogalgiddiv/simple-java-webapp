pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url:'https://github.com/mogalgiddiv/simple-java-webapp.git'
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
                        url: 'http://localhost:9090'
                    )
                ],
                contextPath: '/simpleapp',    
                war: 'target/*.war'
            }
        }
    }
}
