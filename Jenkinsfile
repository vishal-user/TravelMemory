pipeline {
    agent any
    stages {
       stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/vishal-user/TravelMemory.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('backend') {
                    sh '''
                        node -v
                        npm -v
                        npm install
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                dir('backend') {
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline executed successfully.'
        }
        failure {
            echo '❌ Pipeline failed. Check console output.'
        }
        always {
            cleanWs()
        }
    }
}






























