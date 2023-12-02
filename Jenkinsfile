pipeline {
    agent any

    stages {
        stage('Stage1_4322250W') {
            steps {
                echo 'Stage1_4322250W : Release Environment Preparation Completed'
                // Assume release environment setup is done here
            }
        }

        stage('Stage2_4322250W') {
            steps {
                script {
                    // Remove previous container
                    sh 'docker rm -f webapp_4322250w || true'
                    // Create and run the new container
                    sh 'docker run -d --name webapp_4322250w -p 31200:80 wb1_image_4322250w'
                    echo 'Stage2_4322250W : Release Container WebApp_4322250W Created Completed'
                }
            }
        }

        stage('Stage3_4322250W (Parallel)') {
            parallel {
                stage('S3 API Test') {
                    steps {
                        echo 'Stage3_4322250W : API Test Completed'
                        // Assume API test activities here
                    }
                }
                stage('S3 Scan Test') {
                    steps {
                        echo 'Stage3_4322250W : Scan Test Completed'
                        // Assume security scan test activities here
                    }
                }
            }
        }

        stage('Stage4_4322250W') {
            steps {
                script {
                    def userInput = input(id: 'ProceedOrAbort', message: '4322250W, proceed to release the work to next phase?', parameters: [choice(choices: 'Proceed\nAbort', description: 'Select an option', name: 'ProceedOrAbort')])
                    if (userInput == 'Proceed') {
                        echo 'Stage4_4322250W : Work Release – Proceeds to Next Phase'
                    } else {
                        echo 'Stage4_4322250W : Work Release - Stops'
                        currentBuild.result = 'ABORTED'
                        error('Pipeline aborted by user')
                    }
                }
            }
        }

        stage('Stage5_4322250W') {
            steps {
                script {
                    echo 'Stage5_4322250W : Work Release – Proceeds to Next Phase'
                    // Additional actions for the next phase
                }
            }
        }
    }
}
