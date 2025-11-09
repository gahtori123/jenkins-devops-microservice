pipeline {
    agent {
        docker {
            image 'maven:3.6.3'
            args '-v /root/.m2:/root/.m2'   // optional: to cache maven dependencies
        }
    }

    stages {
        stage('Build') {
            steps {
                sh "mvn --version"
                sh "mvn clean package"
                echo "Build Completed"
            }
        }

        stage('Test') {
            steps {
                echo "Running Tests"
                sh "mvn test"
            }
        }

        stage('Integration Test') {
            steps {
                echo "Integration Test Stage Executed"
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
