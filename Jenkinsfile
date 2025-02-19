pipeline {
    agent any  // Runs on an Ubuntu agent

    stages {
        stage('Checkout Repository') {
            steps {
                checkout scm
            }
        }

       stage('Setup .NET') {
            steps {
                dotnetSdkInstall(version: '6.0.100')
            }
        }

        stage('Restore dependencies') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
