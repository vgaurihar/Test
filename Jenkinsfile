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

    }
}
