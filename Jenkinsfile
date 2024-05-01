pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat Web Server') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcatserver', path: '', url: 'http://3.143.5.242:8080/')], contextPath: 'webapp', war: '**/*.war'    
            }
        }
    }
}
