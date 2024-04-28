pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Instalar Docker
                    sh 'sudo apt-get update'
                    sh 'sudo apt-get install -y docker.io'

                    // Construir la imagen Docker
                    sh 'docker build -t docker-react -f Dockerfile.dev .'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Ejecutar las pruebas con Docker
                    sh 'docker run docker-react npm run test -- --coverage'
                }
            }
        }
    }
}
