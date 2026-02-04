pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Install Runtime') {
            steps {
                echo 'Installing Node.js'
                sh '''
                  curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
                  sudo apt-get install -y nodejs
                '''
            }
        }

        stage('Deploy Backend') {
            steps {
                echo 'Deploying backend application'
                sh '''
                  pkill node || true
                  nohup node app.js > backend.log 2>&1 &
                '''
            }
        }
    }
}
