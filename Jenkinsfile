pipeline{
    agent any
    stages{
         // Création image
        stage('Arreter et supprimer mon container cv_eleroy'){
            steps {
                // sh 'docker stop cv_eleroy'
                //sh 'docker rm cv_eleroy'
                sh 'docker rm -f cv_eleroy || true'
            }
            post{
                success {
                    echo "======== Container stop and remove with success =========="
                }
                failure {
                    echo "====++++Docker failed to delete my container++++===="
                }
            }
        }
        // Création image
        stage('Création image docker'){
            steps {
                sh 'docker build -t cv_eleroy .'
            }
            post{
                success {
                    echo "======== Docker image created with success =========="
                }
                failure {
                    echo "====++++Docker image failed++++===="
                }
            }
        }
        stage('Lancer un container de cette image'){
            steps {
                sh 'docker run -d -p 8093:80 --name cv_eleroy_cont cv_eleroy'
            }
             post {
                success {
                    echo "====++++Container started with success++++===="
                }
                failure {
                    echo "====++++Failed to start Container++++===="
                }
            }
        }
    }
}