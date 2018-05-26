
pipeline {
    agent any

    environment {
        MY_BUILD = "build_${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build') {
            steps {
                build job: 'build', parameters: [[$class: 'StringParameterValue', name: 'MY_BUILD_IDENTIFIER', value: "${MY_BUILD}"]]
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }

        stage('Deploy to stage') {
            steps {
                build job: 'deploy', parameters: [[$class: 'StringParameterValue', name: 'MY_BUILD_IDENTIFIER', value: "${MY_BUILD}"]]
            }
        }
        stage('确认测试通过') {
            steps {
                sleep 1
                input '测试是否成功？'
            }
        }
        stage('Deploy to production') {
            steps {
                echo 'Production..'
            }
        }

    }
}