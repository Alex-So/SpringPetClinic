pipeline {
    agent {
        docker { image 'maven:3.8.4-openjdk-11' }
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Alex-So/SpringPetClinic.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Deploy'){
            steps{
                script {
                    // Assuming the workspace inside the Docker container matches Jenkins' default
                    def jarPath = sh(script: 'ls /var/jenkins_home/workspace/${JOB_NAME}/target/*.jar', returnStdout: true).trim()
                    sh "java -jar ${jarPath}"
                }
            }
        }
    }
}
