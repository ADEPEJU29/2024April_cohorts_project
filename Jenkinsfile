pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat Web Server') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tompass', path: '', url: 'http://3.82.246.142:8080/')], contextPath: 'myapp', war: '**/*.war'    
            }
        }
    }
}
