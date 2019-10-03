pipeline {
    agent any

    parameters{
        string(name: 'tomcat-dev', defaultValue: '10.10.10.10', description: 'test parameter1')
        string(name: 'tomcat-prod', defaultValue: '10.10.10.11', description: 'test parameter2')
    }

    triggers{
        pollSCM('* * * * *')
    }

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
