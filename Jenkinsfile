pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'docker-cred'
        DOCKER_IMAGE = 'rhitwik/flask-app'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                        docker.image(DOCKER_IMAGE).push('latest')
                    }
                }
            }
        }

        stage('Verify Workspace') {
            steps {
                bat 'dir'
                bat 'dir k8s'
            }
        }

        stage('Deploy') {
            steps {
                bat 'kubectl apply -f k8s\\'
            }
        }

        stage('Rollout Deployment') {
            steps {
                bat 'kubectl rollout restart deployment/python-webapp -n webapps'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}