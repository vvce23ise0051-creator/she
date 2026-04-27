pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('CHECKOUT') {
            steps {
                git branch: 'main', url: 'https://github.com/vvce23ise0051-creator/she.git'
            }
        }

        stage('Build') {
            steps {
                dir('demo') {
                    bat 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                dir('demo') {
                    bat 'mvn test'
                }
            }
        }
    }

    post {
    success {
        bat 'curl -X POST -H "Content-type: application/json" --data "{\\"text\\":\\"Build SUCCESS\\"}" https://hooks.slack.com/services/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'
    }
    failure {
        bat 'curl -X POST -H "Content-type: application/json" --data "{\\"text\\":\\"Build FAILED\\"}" https://hooks.slack.com/services/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'
    }
}
}
