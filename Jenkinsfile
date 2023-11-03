node {
  stage('SCM') {
    checkout scm
  }
  environment {

    PATH = "C:\\WINDOWS\\SYSTEM32"

}
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScannerDemo_BM'
    withSonarQubeEnv() {
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"SergioAVega_sonarQubeDotNet_AYuRTcoeMv0giqkxllET\""
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
