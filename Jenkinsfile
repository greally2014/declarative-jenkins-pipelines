pipeline {
    agent any
    environment = {
        RELEASE = '20.04'
    }
    stages {
        stage('Build') {
            agent any
            environment {
                LOG_LEVEL = 'INFO'
            }
            steps {
                sh 'echo "This is $BUILD_NUMBER of demo $DEMO"'
            }
        }
        stage('Test') {
            steps {
                echo "Testing release ${RELEASE}"
            }
        }
        stage('Deploy') {
            input {
                message = 'Deploy?'
                ok 'Do it!'
                parameters {
                    string(name: 'TARGET_ENVIRONMENT', defaultValue: 'PROD', description: 'Target deployment environment')
                }
            }
        }
    }
    post {
        always {
            echo 'Prints whether deploy happened or not, success or failure'
        }
    }
}