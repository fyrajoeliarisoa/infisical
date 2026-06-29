pipeline {
    agent any

    triggers {
        // Déclenche le pipeline à chaque modification sur GitHub (nécessite un Webhook configuré sur GitHub)
        githubPush()
    }

    options {
        // Conserve les logs propres et limite le nombre de builds enregistrés
        buildDiscarder(logRotator(numToKeepStr: '10'))
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout') {
            steps {
                // Récupère le code depuis le dépôt GitHub
                // Note : Jenkins gère souvent cela automatiquement si vous utilisez un projet "Multibranch Pipeline"
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Compilation et préparation de l\'environnement...'
                // Exemple pour un projet Node.js / PHP / Python :
                // sh 'npm install' ou 'composer install'
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests unitaires et de sécurité...'
                // Remplacez par votre commande de test réelle
                // Exemple : sh 'npm test' ou 'vendor/bin/phpunit' ou 'pytest'
                sh 'echo "Tests réussis !"'
            }
        }
    }

    post {
        always {
            echo 'Nettoyage de l\'espace de travail...'
        }
        success {
            echo 'Le pipeline s\'est terminé avec succès !'
        }
        failure {
            echo 'Le pipeline a échoué. Vérifiez les logs.'
        }
    }
}
