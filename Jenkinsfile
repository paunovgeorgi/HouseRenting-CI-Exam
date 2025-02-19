pipeline {
    agent { label 'linux' }  // Runs on an Ubuntu agent

    stages {
        stage('Checkout Repository') {
            steps {
                checkout scm
            }
        }

        stage('Setup .NET') {
            steps {
                sh 'wget https://dot.net/v1/dotnet-install.sh -O dotnet-install.sh'
                sh 'chmod +x dotnet-install.sh'
                sh './dotnet-install.sh --version 6.0.0'
                sh 'export PATH=$HOME/.dotnet:$PATH'
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
