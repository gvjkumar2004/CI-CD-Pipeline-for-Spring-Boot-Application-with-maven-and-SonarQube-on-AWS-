pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                url: 'https://github.com/gvjkumar2004/springbootwebapp1.git'
            }
        }
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Deploy') {
            steps {
              {
                    sh 'scp target/spring-boot-web-0.0.1-SNAPSHOT.jar ubuntu@3.110.221.14:/home/ec2-user/'
                    sh 'ssh ubuntu@3.110.221.14 "java -jar /home/ec2-user/spring-boot-web-0.0.1-SNAPSHOT.jar"'
                }
            }
        }
    }
}
