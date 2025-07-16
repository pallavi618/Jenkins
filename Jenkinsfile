pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1' // Make sure this matches your Jenkins tool config
    }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-11-openjdk-amd64'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/pallavi618/jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        // Optional: Deploy stage
        // stage('Deploy') {
        //     steps {
        //         echo 'Deploying to staging...'
        //     }
        // }
    }
}
