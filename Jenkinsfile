pipeline {
  agent any

  environment {
    DOTNET_CLI_HOME = "C:\\Program Files\\dotnet"
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
          bat "dotnet restore"

          echo 'build app'
          bat "dotnet build --configuration Release"
        }
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        // You can add: bat "dotnet test --no-build --configuration Release"
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying application...'
        bat "dotnet publish --no-restore --configuration Release --output .\\publish"
      }
    }
  }

  post {
    success {
      echo 'SUCCESS!'
    }
  }
}
