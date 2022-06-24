pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.6/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/BeaAnt/javaloginapp.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-9.1') { 

        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}
