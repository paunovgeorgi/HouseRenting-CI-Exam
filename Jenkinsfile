pipeline {
    agent any  // Runs on an Ubuntu agent

    tools {
        dotnetsdk 'dotnet6'  // Use the name you configured in Jenkins
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'sudo apt-get update && sudo apt-get install -y libicu-dev'
            }
        }

        stage('Checkout Repository') {
            steps {
                checkout scm
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
