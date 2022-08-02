pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                echo "${env.BUILD_URL}"
            }
        }
        stage('proceed to Deploy') {
            steps {
                script {
                if (env.BRANCH_NAME == "master") {
                    input 'Proceed for Deployment?'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
        }
        success {
            echo 'I succeeded!'
            mail to: 'primiya.vs@gmail.com',
            subject: "Pipeline: ${currentBuild.fullDisplayName}",
            body: "Build URL: ${env.BUILD_URL}"
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}