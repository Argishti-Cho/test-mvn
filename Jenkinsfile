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
                // Run commands
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
                sh 'cd testdir && touch testfile.txt'
            }
        }
    }
}
