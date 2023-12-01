pipeline {
    agent any
    parameters {
        string(name: 'Version', defaultValue: '', description: 'Version to deploy')
        choice(name: 'AvailableVersions', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Select version to deploy')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Execute tests')
    }
    environment {
        New_version = params.Version ?: '' // Using entered version or empty string if not provided
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building Project..'
                echo "Building Version ${New_version}"
                // Here you can define commands for your build
            }
        }
        stage('Test') {
            when {
                expression { params.executeTests }
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
                echo "Deploying version ${env.New_version}..."
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
