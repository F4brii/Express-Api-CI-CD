pipeline {
  agent any
  stages {
    stage('CleanWorkspace') {
        steps {
            cleanWs()
        }
    }
    stage('build and test') {
      steps {
        dir('api'){
            sh 'docker-compose build'
            sh 'docker-compose run --rm web npm run test'
        }
      }
    }
    stage('deploy') {
      steps {
        dir('api'){
            sh 'docker-compose up -d'
        }
      }
    }
  }
}