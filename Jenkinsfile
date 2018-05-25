pipeline {
    agent any
    tools {
        maven 'localMvn'
    }

    stages{
        stage('Build'){
            steps {
                sh 'source /Users/hemanth.haridas/.bash_profile'
                sh 'mvn clean package'
            }
            post {
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }

            }
        }
        stage('Deploy to staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }

    }
}