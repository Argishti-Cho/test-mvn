pipeline {
    agent any

    // Define tools,
    // tools {
    //     maven 'MAVEN3'
    //     jdk 'OracleJDK9'
    // }

    // Define stages
    stages {
        stage('fetching') {
            steps {
                // Clone the Git repository
                git branch: 'master', url: 'https://github.com/Argishti-Cho/test-mvn.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh '''
                #!/bin/bash
                DIR="testdir"
                if [ -d $DIR ]; then
                    echo "$DIR exists"
                else
                    mkdir -p $DIR
                fi
                '''
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                sh 'cd testdir && touch testfile.txt'
            }
            // post {
            //     // Collect test reports
            //     always {
            //         junit 'target/surefire-reports/*.xml'
            //     }
            // }
        }
    }

    post {
        success {
            // Steps to run if the pipeline succeeds
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true

                // Additional command to handle post-success actions
                echo 'Build and Test Stages completed successfully. Artifacts archived.'
            }
        }
        failure {
            // Steps to run if the pipeline fails
            steps {
                echo 'The build or test failed. Check the console output for details.'
            }
        }
    }
}
