pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Integration') {
      steps {
        sh 'dotnet test tests/IntegrationTests'
      }
    }

    stage('Deployment') {
      steps {
        sh '''

set +e dotnet publish eShopOnWeb.sln -o /var/aspnet
'''
      }
    }

  }
}