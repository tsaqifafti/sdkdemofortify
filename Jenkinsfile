pipeline {
	agent any
	environment {
			CONTROLLER_URL = "http://192.168.1.186:8080/scancentral-ctrl"
			VERSION_ID = "10002"
			UPLOAD_TOKEN = "f2a08e91-3e45-4d1f-963a-0efde16f1a31"
	}
	stages {
		stage('Prepare Environment'){
			steps {
				echo "Cek Ketersediaan Maven & Scancentral"
				
				bat 'mvn -v'
				echo "Maven OK"
				
				bat 'cancentral --version'
				echo "Maven OK"
			}
		}
//		stage('Build & Scan'){
//			steps {
//				echo "Build Project Maven & Scan with scancentral SAST"
//				powershell """ scancentral -url ${CONTROLLER_URL} start -bt mvn -upload -versionid ${VERSION_ID} -uptoken ${UPLOAD_TOKEN} """
//			}
//		}
	}	
}