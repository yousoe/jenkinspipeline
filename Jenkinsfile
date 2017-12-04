pipeline {
    agent any

        stages ('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        post {
            success {
                echo 'Now Archiving...'
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                build job: 'Deploy-to-staging'
            }
        }
    }
}
