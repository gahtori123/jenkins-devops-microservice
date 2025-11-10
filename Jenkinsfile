pipeline {
    // agent {
    //     docker {
    //         image 'maven:3.6.3'
    //         args '-v /root/.m2:/root/.m2'   // optional: to cache maven dependencies
    //     }
    // }
    agent any
    environment {
        dockerHome=tool 'myDocker'
        mavenHome = tool 'myMaven'

        PATH="$dockerHome/bin:$mavenHome/bin:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                sh "mvn --version"
                sh "mvn clean package"
                echo "Build"
                echo "PATH-$PATH"
            }
        }

        stage('Compile') {
            steps {
                sh "maven cean compile"
                // sh "mvn test"
            }
        }

        stage('Test') {
            steps {
                 sh "mvn test"
            }
        }

        stage('Integration Test') {
            steps {
               sh "mcn failsafe:integration-test failsafe:verify"
            }
        }
    }

    post {
        always {
            echo "This will always run"
        }
        success {
            echo "This will run only if successful"
        }
        failure {
            echo "This will run only if failed"
        }
    }
}
