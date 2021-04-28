pipeline{
    agent any 
    
    tools{
        maven 'Maven'
    }
   stages{
       stage('clonerepo'){
           steps{
               git 'https://github.com/neelasandeep/CICD.git'
           }
       }
   
       stage('test'){
           steps{
               sh 'mvn test'
           }
       }
       stage('package'){
           steps{
               sh 'mvn package'
           }
       }
       stage('Results'){
           steps{
               junit '**/*.xml'
               archiveArtifacts artifacts: '**/*.war', followSymlinks: false
           }
       }
       stage('deploy'){
           steps{
               deploy adapters: [tomcat8(credentialsId: 'tomcatcreds', path: '', url: 'http://15.206.91.44:8090/')], contextPath: null, war: '**/*.war'
           }
       }
       }

}