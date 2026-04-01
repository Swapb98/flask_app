pipeline {
    agent any
    
    tools {
        sonarRunner 'SonarScanner'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Swapb98/flask_app.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'echo "Building Project...."'
            }
        }
        
        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=demo-project \
                    -Dsonar.sources=.
                    '''
                }
            }
        }
    }
}
