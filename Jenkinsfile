pipeline {
    agent any
    
    environment {
        NODE_ENV = 'production'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Clean workspace and checkout code
                cleanWs()
                git branch: 'main',
                    url: 'https://github.com/benacton/jenkins-nextjs-app.git'
            }
        }
        
        stage('Install') {
            steps {
                sh '''
                    npm install
                    npm install -D tailwindcss postcss autoprefixer
                '''
            }
        }
        
        stage('Build') {
            steps {
                sh '''
                    npm run build
                    ls -la .next
                '''
            }
        }
    }
    
    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
