pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
        maven 'Maven3'
    }

    environment {
        NODE_HOME = tool name: 'NodeJS', type: 'NodeJSInstallation'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-username/my-react-app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test -- --watchAll=false'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
