pipeline {
    agent any

    stages {
        stage("build") {
            steps {
                echo 'building the applications'
                echo 'building the app'
            }
        }

        stage("test") {
            steps {
                echo 'testing the app'
            }
        }

        stage("deploy") {
            steps {
                echo 'deploy the app'
            }
        }
    }

    post {
        // se ejeucta al ultimo de la tuberia
        always {
            // se ejecuta siempre independientemente si sale bien o mal 
        }
        success {
            // se ejecuta si es ok pipeline            
        }
        failure {
            // se ejcuta si falla pipeline
        }
    }
}