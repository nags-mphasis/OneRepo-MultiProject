pipeline {

    agent any

    stages {
        stage('MainProject') {
            steps {
                sh './gradlew :MainProject:build'
            }
        }
        stage('check1') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('SubProject1') {
            steps {
                sh './gradlew :SubProject1:test'
                cucumber buildStatus: 'UNSTABLE',
                reportTitle: 'SubProject1',
                fileIncludePattern: '**/SubProject1.json'
            }
        }
        stage('SubProject2') {
            steps {
                sh './gradlew :SubProject2:test'
                cucumber buildStatus: 'UNSTABLE',
                reportTitle: 'SubProject2',
                fileIncludePattern: '**/SubProject2.json'
            }
        }
        stage('check2') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
