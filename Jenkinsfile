node (label: 'host') {
    stage('Hello') {
        echo 'Hello World'
    }

    stage('Checkout Code'){
            checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ThaiThanh0703/dashy']])
    }
    
    stage('SonarQube Analysis') {
        def scannerHome = tool 'sonarqube';
        withSonarQubeEnv() {
            bat "${scannerHome}/bin\\sonar-scanner" //because the agent 'host' is windows so the path is that
            // if the agent is linux then the command is  {sh "${scannerHome}/bin/sonar-scanner"}
            // if the agent is windows and use sonarscanner for msbuild, then the command is {bat "${scannerHome}\\SonarScanner.MSBuild.exe begin "}

        }
    }
}
