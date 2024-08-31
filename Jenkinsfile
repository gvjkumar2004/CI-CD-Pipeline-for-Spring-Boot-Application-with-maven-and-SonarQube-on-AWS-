pipeline {
    agent any
    environment {
        DEPLOY_SERVER = 'ubuntu@43.205.255.206'
        SONARQUBE_SERVER = 'sonarqube'  // This should match the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/gvjkumar2004/springbootwebapp1.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE_SERVER}") {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Deploy') {
            steps {
                sshagent(['ssh-cred']) {
                    sh '''
                    scp -o StrictHostKeyChecking=no target/*.jar ${DEPLOY_SERVER}:/home/ubuntu/
                    ssh -o StrictHostKeyChecking=no ${DEPLOY_SERVER} "nohup java -jar /home/ubuntu/*.jar > /dev/null 2>&1 &"
                    '''
                }
            }
        }
    }
}
