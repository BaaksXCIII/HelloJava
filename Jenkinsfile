pipeline {
    agent any

    stages {
        stage('Récupérer le dépôt') {
            steps {
                git credentialsId: 'GitHubKey', url: 'https://github.com/MoradDev/HelloJava.git'
            }
        }

        stage('Compilation et exécution') {
            steps {
                sh 'javac Hello.java'

                sh 'java Hello'
            }
        }

        stage('Créer et pousser un tag') {
            steps {
                script {
                    def gitTag = "version_${BUILD_NUMBER}"
                    sh "git tag ${gitTag}"
                    sh "git push origin/master ${gitTag}"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès.'
        }
        failure {
            echo 'Pipeline échoué.'
        }
    }
}
