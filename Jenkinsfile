pipeline {
    agent any

    // Define tools
    tools {
        maven 'Maven'  
        jdk 'JDK'
    }

    // Define stages
    stages {
        stage('Checkout') {
            steps {
                // Clone the Git repository
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean install -DskipTests' // Skipping tests here to run them in a separate stage
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
            post {
                // Collect test reports
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            // Steps to run if the pipeline succeeds
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true

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
