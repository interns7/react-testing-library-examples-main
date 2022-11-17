pipeline {
    agent {
        node {
            label 'sonar'
        }
    }

    options {
        buildDiscarder logRotator(
                    daysToKeepStr: '16',
                    numToKeepStr: '10'
            )
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh '''
                echo "Cleaned Up Workspace For Project"
                '''
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://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@github.com/interns7/react-testing-library-examples-main.git']]
                ])
            }
        }

        stage(' Unit Testing') {
            steps {
                sh '''
                echo "Running Unit Test"
                '''
            }
        }

        stage('Code Analysis') {
            steps {
                sh '''
                echo "Running Code Analysis"
                '''
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh '''
                echo "Building Artifact"
                '''

                sh '''
                echo "Deploying Code"
                '''
            }
        }
    }
}
