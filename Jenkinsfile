pipeline {
    agent any
    environment {
        DOCKER_COMPOSE_VERSION = '2.27.0'
        PATH = "/usr/local/bin:$PATH" // Assurez-vous que cela inclut le chemin vers Docker
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'docker --version' // Vérifier que Docker est accessible
                    // Lancement de Docker Compose
                    sh 'docker-compose up -d --build'
                }
            }
        }
        // stage('Test') {
        //     steps {
        //         script {
        //             // Mettez ici vos commandes pour exécuter des tests
        //             echo "Running tests"
        //             sh 'curl -s http://localhost:8000'
        //         }
        //     }
        // }
        // stage('Test Deploy') {
        //     steps {
        //         script {
        //             // Mettez ici vos commandes pour déployer l'application
        //             echo "Deploy"
        //         }
        //     }
        // }
    }
    post {
        success {
            // Nettoyer les ressources Docker
            sh'docker-compose down -v'

            emailext body: 'coach pas de 6iem na leer : Success', subject: 'Detail du Build', to: 'gorisowrg9@gmail.com'

        }
        failure {
            emailext body: 'coach pas de 6iem: Echec', subject: 'Detail du Build', to: 'gorisowrg9@gmail.com'

        }
    }
} 
