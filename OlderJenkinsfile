pipeline {
    agent any
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "This is Initialize stage"
                '''
            }
        }
        stage ('Build') {
            steps {
                sh '''
                    echo "This is Build stage"
                    echo 'Hello Vaibhav!'
                '''
            }
        }
    }
}
