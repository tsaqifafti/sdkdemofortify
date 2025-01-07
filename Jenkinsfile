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
				script {
				powershell 'mvn -v; if ($?) { Write-Output "Maven OK" } else {exit 1}'
				}
				powershell 'scancentral --version; if ($?) { Write-Output "Scancentral OK" } else {exit 1}'
			}
		}
	}
	stages {
		stage('Build & Scan'){
			steps {
				echo "Build Project Maven & Scan with scancentral SAST"
				powershell """ scancentral -url ${CONTROLLER_URL} start -bt mvn -upload -versionid ${VERSION_ID} -uptoken ${UPLOAD_TOKEN} """
			}
		}
	}
}