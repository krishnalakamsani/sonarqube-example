pipeline{
    agent {label 'agent2_jfrog'}
    stages{
       stage('Git Checkout Stage'){
            steps{
                git branch: 'main', credentialsId: 'gitprivate', url: 'https://github.com/krishnalakamsani/sonar-example'
            }
         }        
       stage('Build Stage'){
            steps{
                sh 'mvn clean install'
            }
         }
        stage('SonarQube Analysis Stage') {
            steps{
                withSonarQubeEnv('sonarqube') { 
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sonar-test1"
                }
            }
        }
    }
}
