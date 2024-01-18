pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Integration') {
      parallel {
        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('Unit') {
          steps {
            sh '''

set +e dotnet  test tests/UnitTests
'''
          }
        }

        stage('Functional') {
          steps {
            sh '''

set +e dotnet    test tests/FunctionalTests
'''
          }
        }

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