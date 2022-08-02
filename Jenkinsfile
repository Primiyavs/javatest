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
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
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