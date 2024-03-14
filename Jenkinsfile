pipeline {
    agent any

    triggers {
        cron('H/10 * * * 4') // Trigger every 10 minutes on Thursdays
    }

    stages {
        stage('Build') {
            steps {
                // Add steps to build the project and generate the artifact
                bat 'mvn clean package' // Execute Maven command using 'bat' step
            }
        }

        stage('Generate Code Coverage Report') {
            steps {
                // Add steps to generate code coverage report using Jacoco
                bat 'mvn jacoco:report' // Execute Jacoco command using 'bat' step
            }
            post {
                always {
                    // Archive Jacoco report as a build artifact
                    archiveArtifacts artifacts: 'target/site/jacoco/index.html', fingerprint: true
                }
            }
        }
    }
}

