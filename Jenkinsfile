pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh 'gp++ -o PES2UG22CS601-1 hello.cpp'  // Intentional error: 'g++' misspelled as 'gp++'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS601-1'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'git config --global user.name "Surabhi S Suvarna"'
                    sh 'git config --global user.email "surabhisuvarna290804@gmail.com"'
                    sh 'git checkout main'
                    sh 'git add -A'
                    sh 'git commit -m "Added hello.cpp file" || echo "No changes to commit"'
                }
            }
        }
    }

    post {
        success {
            echo "Build and deployment successful!"
        }
        failure {
            echo "Pipeline failed"  // This will be executed if any stage fails
        }
    }
}
