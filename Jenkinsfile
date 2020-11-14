pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        sh 'mvn -B clean install'
      }
    }

    stage('Reporting') {
      parallel {
        stage('SonarQube') {
          steps {
            sh 'mvn -B sonar:sonar -Dsonar.host.url=TODO'
          }
        }

        stage('Javadoc build') {
          steps {
            sh 'mvn -B javadoc:javadoc'
          }
        }

      }
    }

    stage('Artifact Upload') {
      steps {
        sh 'mvn -B deploy'
      }
    }

  }
}