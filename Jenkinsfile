pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/gurumee92/charts.git', branch: 'main' 
      }
    }

    stage('docker ps') {
      steps {
        sh '''
        docker ps
        '''
      }
    }
  }
}
