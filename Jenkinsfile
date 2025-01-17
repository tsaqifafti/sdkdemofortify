pipeline {
	agent any
	environment {
//			CONTROLLER_URL = "http://192.168.1.183:8081/scancentral-ctrl"
//			VERSION_ID = "10002"
//			UPLOAD_TOKEN = "f2a08e91-3e45-4d1f-963a-0efde16f1a31"
			TARGET_DIR = "C:\\Users\\Administrator\\Downloads\\FortifyAWSJavaSDKDemo-master\\FortifyAWSJavaSDKDemo-master"
	}
	stages {
		stage('Prepare Environment'){
			steps {
				echo "Cek Ketersediaan Maven & Scancentral"
				
				bat 'mvn -v'
				
				bat 'scancentral --version'
			}
		}
		stage('Build & Scan'){
		steps {
				echo "Build Project Maven & Scan with scancentral SAST"

				dir ("${TARGET_DIR}") {
					bat 'scancentral -url http://192.168.1.186:8080/scancentral-ctrl start -bt mvn -upload -versionid 10002 -uptoken f2a08e91-3e45-4d1f-963a-0efde16f1a31'
				}
			}
		}
	}	
}