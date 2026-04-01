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
                    docker run --rm \
                        -e SONAR_HOST_URL=http://http://192.168.29.225/:9000 \
                        -v $(pwd):/usr/src \
                        sonarsource/sonar-scanner-cli \
                        -Dsonar.projectKey=demo-project \
                        -Dsonar.sources=.
                    '''
                }
            }
        }
    }
}
