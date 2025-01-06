pipeline {
    // Use the 'agent' directive to define the execution environment
	  agent any
//    agent {
//        label 'build-agent' // Specify a specific agent/node label
//    }

    // Define global environment variables for consistency
//    environment {
//        BUILD_TIMESTAMP = "${new Date().format('yyyy-MM-dd_HH-mm-ss')}" // Timestamp for logs/artifacts
//        APP_NAME = 'MyApplication' // Example application name
//    }
//
    // Set up options for build timeout and logging
//    options {
//       timeout(time: 30, unit: 'MINUTES') // Avoid hanging builds
//        timestamps() // Add timestamps to logs for easier debugging
//        ansiColor('xterm') // Colorize console output
//    }

    stages {
        // Stage 1: Prepare environment
        stage('Prepare') {
            steps {
                script {
                    echo "Preparing environment for ${APP_NAME}..."
                }
            }
        }

        // Stage 2: Checkout source code from repository
        stage('Checkout Code') {
            steps {
                checkout scm // Use source code from the job's configuration
                script {
                    echo "Code checked out successfully."
                }
            }
        }

        // Stage 3: Build application
        stage('Build') {
            steps {
                script {
                    echo "Building ${APP_NAME}..."
                }
            }
        }

        // Stage 4: Run tests
        stage('Test') {
            steps {
                script {
                    echo "Running tests for ${APP_NAME}..."
                }
            }
        }

        // Stage 5: Package application (optional)
        stage('Package') {
            steps {
                script {
                    echo "Packaging ${APP_NAME}..."
                }
            }
        }

        // Stage 6: Deploy application (optional)
        stage('Deploy') {
            when {
                branch 'main' // Only deploy from the main branch
            }
            steps {
                script {
                    echo "Deploying ${APP_NAME}..."
                    sh './deploy.sh' // Example deployment script
                }
            }
        }
    }

    // Post-actions for cleanup and notifications
    post {
        always {
            echo "Cleaning up workspace..."
            cleanWs() // Clean workspace after every build
        }

        success {
            echo "Build completed successfully at ${BUILD_TIMESTAMP}."
        }

        failure {
            echo "Build failed. Please check logs for more details."
        }

        unstable {
            echo "Build is unstable. Review warnings or test results."
        }

        aborted {
            echo "Build was aborted by user or timeout."
        }
    }
}
