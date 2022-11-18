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
                // checkout([
                //     $class: 'GitSCM',
                //     branches: [[name: '*/main']],
                //     userRemoteConfigs: [[url: 'https://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@github.com/interns7/react-testing-library-examples-main.git']]
                // ])
                script {
                    cleanWs()
                    git clone -b 'dev' 'https://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@github.com/interns7/react-testing-library-examples-main.git'
                }
            }
        }

        stage(' Unit Testing') {
            steps {
                sh '''
                echo "Running Unit Tests"
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
