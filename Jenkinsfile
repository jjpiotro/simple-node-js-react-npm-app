pipeline{
    agent{
        docker{
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }

    environment{
        CI = 'true'
    }

    stages{
        stage("Build"){
            steps{
                echo "========executing Build========"
                sh 'npm install'
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========Build executed successfully========"
                }
                failure{
                    echo "========Build execution failed========"
                }
            }
        }
        stage("Test"){
            steps{
                echo "====++++executing Test++++===="
                sh './jenkins/scripts/test.sh'
            }
            post{
                always{
                    echo "====++++always++++===="
                }
                success{
                    echo "====++++Test executed succesfully++++===="
                }
                failure{
                    echo "====++++Test execution failed++++===="
                }
        
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}