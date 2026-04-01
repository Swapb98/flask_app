pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Swapb98/flask_app.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'echo "Building Project...."'
            }
        }
        
        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=demo-project \
                    -Dsonar.host.url=192.168.29.225:9000 \
                    -Dsonar.sources=.
                    '''
                }
            }
        }
    }
}
