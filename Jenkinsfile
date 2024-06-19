pipeline {
    agent { label 'default' }
    parameters {
        string(name: 'Micketto', defaultValue: 'from Micketto', description: 'Hello from Micketto')
    }

    environment {
        CREDENTIALS = credentials('github-credentials')

    }

    triggers {
        cron('H/15 * * * *')

    }

    stages {
        stage('Write File') {
            steps {
                script {
                    def content = "Hello+${params.Micketto}"
                    writeFile(file: 'result.txt', text: content)
                }
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'result.txt', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
