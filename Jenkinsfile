pipeline {
    agent any
    tools{maven 'Maven 3.6.3'}
    stages {
        stage('Checkouut') {
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
                sh 'java -jar /var/lib/jenkins/workspace/PetClinicDeclaretedPipepline/target/*.jar'
            }
        }
    }
}
