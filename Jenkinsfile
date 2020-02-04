pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Prepare') {
            agent {
                docker { image 'node:alpine' }
            }
            steps {
                dir('code/frontend') {
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            agent {
                docker { image 'node:alpine' }
            }
            steps {
                dir('code/frontend') {
                    sh 'npm run build'   
                }
            }
        }
        stage('Static Analysis') {
            agent {
                docker { image 'node:alpine' }
            }
            steps {
                echo 'Analyze'
                // sh 'npm run lint'
            }
        }
        stage('Unit Test') {
            agent {
                docker { image 'node:alpine' }
            }
            steps {
                echo 'Test'
                // sh 'npm run test'
            }
        }
        stage('e2e Test') {
            steps {             
                echo 'e2e Test'
            }
            post {
                always {
                    echo 'Cleanup'
                }
            }
        }
        stage('Deploy') {
            steps {                
                echo 'Deploy'
            }
        }
    }
}
