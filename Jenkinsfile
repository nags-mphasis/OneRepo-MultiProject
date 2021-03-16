pipeline {

    agent any

    stages {
        stage('build') {
            steps {
                sh './gradlew clean build'
            }
        }
        stage('check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
/*        stage('Smoke Test') {
            steps {
                sh './gradlew clean test -Dcucumber.options="src/test/resources/SmokeTest/SmokeTest.feature"'
                cucumber buildStatus: 'UNSTABLE',
                reportTitle: 'Smoke Test',
                fileIncludePattern: '**/Smoke.json'
            }
        }
        stage('Sanity Test') {
            steps {
                sh './gradlew clean test -Dcucumber.options="src/test/resources/SanityTest/SanityTest.feature"'
                cucumber buildStatus: 'UNSTABLE',
                reportTitle: 'Sanity Test',
                fileIncludePattern: '**/Sanity.json'
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        } */
    }
    
    post {
        always {
            cleanWs()
        }
    }
}