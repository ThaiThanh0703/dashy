pipeline {
    agent {
        label 'host'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Checkout Code'){
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ThaiThanh0703/dashy']])
            }
        }

        stage('SonarQube Analysis') {
            def scannerHome = tool 'SonarQube Scanner';
            withSonarQubeEnv() {
                sh "${scannerHome}/bin/sonar-scanner" \
                -D sonar.projectKey=dashy \
                -D sonar.sources=./
            }
        }
    }
}