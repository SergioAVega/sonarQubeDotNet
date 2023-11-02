node {
  stage('SCM') {
    git 'https://github.com/SergioAVega/sonarQubeDotNet'
  }
  stage('Build + SonarQube analysis') {
    def sqScannerMsBuildHome = tool 'Default MSBuild'
    withSonarQubeEnv('Jenkins') {
      bat "${sqScannerMsBuildHome}\\SonarQube.Scanner.MSBuild.exe begin /k:SergioAVega_sonarQubeDotNet_AYuRTcoeMv0giqkxllET"
      bat 'MSBuild.exe /t:Rebuild'
      bat "${sqScannerMsBuildHome}\\SonarQube.Scanner.MSBuild.exe end"
    }
  }
}
