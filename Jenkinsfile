pipeline {
   
    agent { 
        
        docker {
            image 'docker-node20'
            reuseNode true
            label 'alserver2'
            args '-u 0:0 -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Build') {
            steps {
                script {
                    
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
