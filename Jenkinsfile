pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/gvjkumar2004/springbootwebapp1.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp target/spring-boot-web-0.0.1-SNAPSHOT.jar ubuntu@15.207.71.106:/home/ubuntu/'
                sh 'ssh ubuntu@15.207.71.106 "java -jar /home/ubuntu/spring-boot-web-0.0.1-SNAPSHOT.jar"'
            }
        }
    }
}
