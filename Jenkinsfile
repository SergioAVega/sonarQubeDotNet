pipeline {
    agent any // Use any available agent (no need to specify a label)

    stages {
        stage('SCM') {
            steps {
                script {
                    // Define the custom Git tool 'CustomGitTool'
                    def customGitTool = tool name: 'Git', type: 'hudson.plugins.git.GitTool'

                    // Checkout the source code using the custom Git tool
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/SergioAVega/sonarQubeDotNet']], gitTool: customGitTool])
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScannerDemo_BM' // Assuming SonarScannerDemo_BM tool is correctly configured

                    withSonarQubeEnv() {
                        bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"SergioAVega_sonarQubeDotNet_AYuRTcoeMv0giqkxllET\""
                        bat "dotnet build"
                        bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
                    }
                }
            }
        }
    }
}
