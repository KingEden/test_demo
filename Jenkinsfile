pipeline {
    agent any
    tools {
        
        maven "Maven"
    }
    environment {
        New_version = '1.3.0'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building Project..'
                echo "Building Version ${env.New_version}"
                sh "nvm install"
                // Here you can define commands for your build
            }
        }
        stage('Test') {
            when {
                expression { currentBuild.result == 'ABORTED' }
            }
            steps {
                echo 'Testing..'
                // Here you can define commands for your tests
            }
        }
        stage('Deploy') {
            when {
                expression { env.DEPLOY_STATUS == 'SUCCESS' }
            }
            steps {
                echo "Deploying...."
                // Here you can define commands for your deployment
            }
        }
    }
    post {
        always {
            echo 'Post build condition running'
        }
        failure {
            echo 'Post Action if Build failed'
        }
    }
}
