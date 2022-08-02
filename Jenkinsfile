pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo '${env.BUILD_URL}'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('proceed to Deploy') {
            steps {
                script {
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
        mail to: 'primiya.vs@gmail.com',
        subject: "Pipeline: ${currentBuild.fullDisplayName}",
        body: "Build URL: ${env.BUILD_URL}"
            }
    }
}