pipeline {
    agent any
    environment {
        SONAR_HOST_URL = 'http://localhost:9000/'
    }
    tools {
                maven 'mvn1'
                
            }
    stages {
        stage('checkout'){
            steps {
                echo "hi vivek mahendra welcome to jenkinsffa"
                git url:"https://github.com/vivekmprac/webapp.git", branch: "master"      
            }
        }
        stage('build'){
             steps {
                bat 'mvn clean package'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    bat 'mvn clean verify sonar:sonar'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
