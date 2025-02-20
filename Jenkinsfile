pipeline {
//  agent { label 'master' }  // Menjalankan pipeline di master node
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
        fortifyRemoteAnalysis remoteAnalysisProjectType: fortifyMaven(buildFile: 'custom-pom.xml'),
          remoteOptionalConfig: [notifyEmail: 'admin@company.com', 
          customRulepacks: 'CustomRules.xml'],
          uploadSSC: [appName: 'MyMavenApp', appVersion: '1.0']
      }
    }
  }
}