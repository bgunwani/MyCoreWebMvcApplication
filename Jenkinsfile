pipeline {
    agent any

    tools {
        git "Default"  // This will use the Git tool configuration you set earlier in Jenkins' Global Tool Configuration
    }

    environment {
        DOTNET_CLI_HOME = "C:\\Program Files\\dotnet"  // Optional, remove if not needed
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Restoring dependencies
                    bat "dotnet restore"

                    // Building the application
                    bat "dotnet build --configuration Release"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Running tests without restoring dependencies
                    bat "dotnet test --no-restore --configuration Release"
                }
            }
        }

        stage('Publish') {
            steps {
    
