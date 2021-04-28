pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/neelasandeep/CICD', branch: 'master')
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'mvn test'
          }
        }

        stage('package') {
          steps {
            sh 'mvn package'
          }
        }

      }
    }

  }
}