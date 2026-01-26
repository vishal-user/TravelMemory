pipeline {
    agent any

    tools {
        nodejs 'NodeJS'   // Jenkins → Global Tool Configuration → NodeJS
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/vishal-user/TravelMemory.git'
            }
        }

        stage('Verify Project Structure') {
            steps {
                sh '''
                    if [ ! -d "backend" ]; then
                        echo "ERROR: backend directory not found!"
                        ls -la
                        exit 1
                    fi
                '''
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



























