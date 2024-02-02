pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('tests/Shell Script') {
      parallel {
        stage('unit') {
          steps {
            sh 'dotnet test tests/unitTests'
          }
        }

        stage('integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('functional') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}