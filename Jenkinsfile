pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage('DeployToStaging') {
            when {
                branch 'master'
            }
            environment {
                DEPLOY_CREDS = credentials('webserver_login')
            }
            steps {
                echo '$DEPLOY_CREDS_USR'
            }
        }
    }
}
