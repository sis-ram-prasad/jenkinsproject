pipeline {
    agent {
        dockerContainer {
            image 'maven:3.9.6-eclipse-temurin-17'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}
