pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Pull the latest code from GitHub
                git url: 'https://github.com/janakniraula/django-todo-CICD.git', branch: 'main'
            }
        }
        stage('Deploy') {
            steps {
                // Navigate to the workspace directory
                dir('/var/jenkins_home/workspace/todo-app') {
                    // Stop and remove existing containers
                    sh 'docker-compose down || true'
                    // Rebuild and start containers with the latest code
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed!'
        }
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
