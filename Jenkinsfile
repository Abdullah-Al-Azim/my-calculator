pipeline {
    agent any

    stages {
        stage('Install Python') {
            steps {
                sh '''
                    apt-get update -qq
                    apt-get install -y python3 python3-pip -qq
                    python3 --version
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install pytest --break-system-packages --quiet'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest test_calculator.py -v'
            }
        }

        stage('Deploy') {
            steps {
                echo "Build #${BUILD_NUMBER} deployed successfully!"
                echo "Triggered by GitHub push - this is real CD!"
            }
        }
    }

    post {
        success { echo 'Pipeline successful!' }
        failure { echo 'Something went wrong!' }
    }
}
