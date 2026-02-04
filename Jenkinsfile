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
                  cd ~
                  if [ ! -d backendvm ]; then
                    git clone https://github.com/shailu-3126/backendvm.git
                  else
                    cd backendvm && git pull
                  fi
                  cd backendvm
                  pkill node || true
                  nohup node app.js > backend.log 2>&1 &
                EOF
                '''
            }
        }
    }
}

