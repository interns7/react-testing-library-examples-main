pipeline {
    agent { node {label 'Master_Machine'}}
    environment {
        repo_URL = 'https://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@github.com/interns7/react-testing-library-examples-main.git'
        repo_Branch = 'dev'
        prjectKey = 'ui_react_coverage'
        sonarHostUrl = 'http://10.2.0.6:9000'
        sonarToken = '34598578a009cac73f33beb160e4496e371731b8'
        emailRecipent = 'akshaya.malik@newgensoft.com,firoz.khan@newgensoft.com,tarun.gulyani@newgensoft.com,virendra.sah@newgensoft.com,shailesh.bist@newgensoft.com,aakash.r@newgensoft.com,vineet.verma@newgensoft.com,pratik.paliwal@newgensoft.com'
       //emailRecipent = 'firoz.khan@newgensoft.com,aakash.r@newgensoft.com,shailesh.bist@newgensoft.com'

    }

    stages {
        stage ('Sonar scan'){
            agent { node {label 'Sonar'}}
            steps {
                script {
                    cleanWs()
                    sh label: '', script: '''cd /datadrive/jenkins/ui
                    rm -r -f react-testing-library-examples-main/'''
                    
                    sh label: '', script: """cd /datadrive/jenkins/ui
                    git clone -b ${env.repo_Branch} ${env.repo_URL}"""

                }
            }
        }
    }

}