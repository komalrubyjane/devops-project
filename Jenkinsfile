pipeline {
    agent any
    
    tools {
        nodejs "node16"
    }
    
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/node-sample-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Deploy to Local Server') {
            steps {
                sh '''
                rm -rf /var/www/nodeapp/*
                cp -r * /var/www/nodeapp/
                cd /var/www/nodeapp
                npm install
                pm2 stop nodeapp || true
                pm2 start server.js --name nodeapp
                '''
            }
        }
    }
}
