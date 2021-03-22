pipeline {
    agent any
    
    environment {
        registry = "chzgustavo/node-helloworld"
        registryCredential = 'docker_hub_login'
        dockerImage = ''
    }

    stages {
        stage("Test") {
            steps {
                echo 'test the apps'
            }
        }

        stage("Build Docker Image") {
            steps {
                script {
                  dockerImage = docker.build registry + ":latest"
                }  
            }
        }

        stage("Push docker image") {
            steps {
                script {
                    docker.withRegistry('', registryCredential) {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        // se ejeucta al ultimo de la tuberia
        always {
            // se ejecuta siempre independientemente si sale bien o mal 
            echo 'always'
        }
        success {
            // se ejecuta si es ok pipeline
                echo 'success'
        }
        failure {
            // se ejcuta si falla pipeline
            echo 'failure'
        }
    }
}