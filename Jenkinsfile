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
                echo 'test the app'
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
                        //dockerImage.push("${env.BUILD_NUMBER}")
                        dockerImage.push()
                    }
                }
            }
        }

        stage("Deploy in cluster") {
            steps {
                echo 'deploy the application'
                script {
                    kubernetesDeploy(kubeconfigId: 'kube-config-minikube', configs: 'deployment.yaml')
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