pipeline {
    agent any

    environment {
        GIT_CREDENTIALS_ID = 'github-creds'
        GIT_REPO_URL = 'https://github.com/piterflow/Proyecto_jenkins.git'
    }

    stages {
        stage('Preparar') {
            steps {
                echo 'Iniciando pipeline...'
            }
        }

        stage('Commit y Push a GitHub') {
            steps {
                script {
                    // Configura Git
                    sh 'git config user.name "Jenkins CI"'
                    sh 'git config user.email "aruicab200@g.educaand.es"'

                    // Añade y hace commit
                    sh 'git add .'
                    sh 'git commit -m "Cambios automáticos desde Jenkins" || echo "Nada que commitear"'

                    // Push usando las credenciales de Jenkins
                    withCredentials([usernamePassword(credentialsId: "${env.GIT_CREDENTIALS_ID}", usernameVariable: 'GIT_USER', passwordVariable: 'GIT_PASS')]) {
                        sh 'git push https://${GIT_USER}:${GIT_PASS}@github.com/piterflow/Proyecto_jenkins.git HEAD:main'
                    }
                }
            }
        }
    }
}
