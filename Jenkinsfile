pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy Backend to backend-vm') {
            steps {
                sh '''
                ssh sn312623@34.29.195.253 << 'EOF'
                  set -e
                  pkill node || true
                  rm -rf backendvm
                  git clone https://github.com/shailu-3126/backendvm.git
                  cd backendvm
                  node -v
                  nohup node app.js > backend.log 2>&1 &
                EOF
                '''
            }
        }
    }
}
