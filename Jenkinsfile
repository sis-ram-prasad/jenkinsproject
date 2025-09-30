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
  
  stages {
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
