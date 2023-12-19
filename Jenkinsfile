pipeline {
    agent any
    
    environment {
        PATH = "$PATH:/opt/apache-maven-3.9.6/bin/"
    }
    
    stages {
        stage('GetCode') {
            steps {
                git branch: 'master', url: 'https://github.com/nenavathsrinu/sample-java-programs.git'
            }
        }
        
        stage("Build") {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonar-server-7.8') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}
