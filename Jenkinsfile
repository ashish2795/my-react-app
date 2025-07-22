pipeline {
    agent any

    environment {
        NODE_ENV = 'production'
    }

    tools {
        nodejs "NodeJS_20"  // Ensure this name matches the tool in Jenkins config
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/ashish2795/my-react-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        // Optional stage
        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }

        // Optional deployment stage
        // stage('Deploy') {
        //     steps {
        //         sh 'scp -r build/ user@server:/var/www/html'
        //     }
        // }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
