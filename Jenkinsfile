pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'docker-cred'
        KUBECONFIG_CREDENTIALS_ID = 'k8-cred2'
        DOCKER_IMAGE = 'rhitwik/flask-app'   // ✅ your image
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
                sh 'ls -l'
                sh 'ls -l k8s'
            }
        }

        stage('Deploy') {
            steps {
                withKubeConfig([credentialsId: KUBECONFIG_CREDENTIALS_ID]) {
                    sh 'kubectl apply -f k8s/'
                }
            }
        }

        stage('Rollout Deployment') {
            steps {
                withKubeConfig([credentialsId: KUBECONFIG_CREDENTIALS_ID]) {
                    sh 'kubectl rollout restart deployment/python-webapp -n webapps'
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}