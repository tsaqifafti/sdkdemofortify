pipeline {
  agent any

  stages {
    stage('Fortify Remote Arguments') {
      steps {
        fortifyRemoteArguments transOptions: '-Xmx4G', 
          scanOptions: '"-analyzers" "dataflow"'
      }
    }

    stage('Fortify Remote Analysis') {
      steps {
        fortifyRemoteAnalysis remoteAnalysisProjectType: fortifyMaven(buildFile: 'pom.xml', skipBuild: false), // Pastikan build dijalankan
          uploadSSC: [appName: 'sdkdemo', appVersion: '1']
      }
    }
  }
}