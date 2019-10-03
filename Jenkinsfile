pipeline {
    agent any
    stages {
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo "succesfully build package. See in target directory"
                    echo "now archieving ..."
                }
            }
        }
        stage('Deploy to staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }
        stage('Deploy to Production'){
            steps {
                timeout(time:5, unit:'DAYS'){
                    input message: 'Approve Production Deployment?'
                }
                build job: 'deploy-to-production'
            }
            post {
                success {
                    echo 'Code deployed to production'
                }
                failure {
                    echo 'Code Deployment failed'
                }
            }
        }
    }
}
