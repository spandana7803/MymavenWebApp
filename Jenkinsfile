pipeline {
    agent any  

    tools {
        maven 'Maven'  
    }

    stages {
        stage('Clean Workspace') {
            steps {
                deleteDir()   // 🔥 clears old code
            }
        }

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/spandana7803/MymavenWebApp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add real deployment here
            }
        }    
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
