pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage("Unit Tests") {
            steps {
                sh './mvnw test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline has ended'
            junit('**/surefire-reports/**/*.xml')
        }
        success {
            echo 'The pipeline was successful'
        }
        failure {
            echo 'The pipeline failed'
        }
        unstable {
            echo 'The pipeline is unstable'
        }
        changed {
            echo 'The pipeline state has changed'
        }
    }
}
