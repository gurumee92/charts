pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/gurumee92/charts.git', branch: 'main' 
      }
    }

    stage('kubectl get ns') {
      agent { docker 'rancher/kubectl:v1.23.7' }
      steps {
        sh '''
        kubectl get ns
        '''
      }
    }
  }
}
