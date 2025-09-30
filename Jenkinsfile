pipeline {
  agent {
    dockerContainer {
      image 'mcr.microsoft.com/dotnet/sdk:8.0'  
    }
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        echo 'Building the project...'
        sh "dotnet restore"
        sh "dotnet build --configuration Release"
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh "dotnet test --no-build --configuration Release"
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying application...'
        sh "dotnet publish --no-restore --configuration Release --output ./publish"
      }
    }
  }

  post {
    success {
      echo 'SUCCESS!'
    }
  }
}
