pipeline {
    agent any

    tools {
        // Install the Maven version configured as "Maven" and add it to the path.
        maven "Maven"
    }

    stages {
        stage('clone') {
            steps {
                // Get clone from a GitHub repository
                git credentialsId: 'e92b2325-2a7e-4340-8bc6-ab9b0b834472', url: 'https://github.com/AnuguPavani/maven-project1.git'
                }
            }
            stage('Build') {
            steps {
                //maven build
                sh ' mvn clean install'
                }
            }
            stage('Deploy') {
            steps {
                //deploy to tomcat
               deploy adapters: [tomcat9(credentialsId: '424b95a9-5aa8-4dc3-b5b8-f0e4cac60260', path: '', url: 'http://192.168.20.133:8081/')], contextPath: 'deploy-mavenproject1.war', war: '**/*.war'
                }
            }
    }
}
