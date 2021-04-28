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
            withMaven(maven: 'Maven', globalMavenSettingsConfig: 'Maven') {
              sh 'mvn test'
            }

          }
        }

        stage('package') {
          steps {
            withMaven(globalMavenSettingsConfig: 'Maven', maven: 'Maven') {
              sh 'mvn package'
            }

          }
        }

      }
    }

  }
}