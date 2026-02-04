pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy Backend (PM2 + Secure SSH)') {
            steps {
                sshagent(['backend-ssh-key']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no sn312623@34.29.195.253 << 'EOF'
                    set -e
                    cd ~

                    if [ ! -d backendvm ]; then
                      git clone https://github.com/shailu-3126/backendvm.git
                    fi

                    cd backendvm
                    git pull

                    pm2 restart backend || pm2 start app.js --name backend
                    pm2 save
                    EOF
                    '''
                }
            }
        }
    }
}

