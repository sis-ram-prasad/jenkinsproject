pipeline {
  agent any

  environment {
    DOTNET_CLI_HOME = "/usr/share/dotnet" // path for Linux agents (adjust if needed)
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
        script {
          echo 'restoring dotnet...'
          sh "dotnet restore"

          echo 'build app'
          sh "dotnet build --configuration Release"
        }
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
