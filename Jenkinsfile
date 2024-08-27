pipeline {
    agent any
    environment {
        DEPLOY_SERVER = 'ubuntu@13.201.30.89'
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
